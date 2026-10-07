# Plan: Issue #61 health check SQLAlchemy error

## Diagnosis

My Unit 2 reproduction did not reproduce the reported SQLAlchemy `ArgumentError`. On commit `f89c06f`, my environment returned `503 Service Unavailable`; PostgreSQL reported `database "pathreview" does not exist`, and the vector database failed because `np.float_` was removed in NumPy 2.0.

The issue thread contains other reproductions of the reported SQLAlchemy error on the same commit. My own reproduction did not reach the database health-check query, so I will not claim that I personally observed that error.

## Scope

I will fix the seeded SQLAlchemy health-check bug and only make the directly related test and type-check configuration changes required for that fix.

Files expected to change:

- `api/routes/health.py`
- A new focused health-check test under `tests/`
- `pyproject.toml` to remove the `api.routes.health` `call-overload` mypy suppression

I will not make unrelated Redis, vector database, or dependency changes.

## Approach

1. Inspect `api/routes/health.py` and the existing test structure under `tests/`.
2. At `api/routes/health.py:32`, change `await db.execute("SELECT 1")` to `await db.execute(text("SELECT 1"))` and import `text` from SQLAlchemy.
3. Add a focused unit test for the database health probe because the repository does not currently contain a dedicated health-check test. The test will use a mocked database session and verify that the probe passes a SQLAlchemy `TextClause` created from `"SELECT 1"` to `db.execute()`.
4. Remove the `api.routes.health` `call-overload` suppression from the mypy configuration in `pyproject.toml`.
5. Run the new focused health-check test and verify that it passes.
6. Run the relevant mypy check and verify that `api.routes.health` no longer requires the `call-overload` suppression.
7. Run the available reproduction setup with `alembic upgrade head` and the application started directly. If the environment still prevents the full endpoint from running, record that limitation instead of claiming the issue was reproduced or fixed.
8. Keep the branch as `fix/61-health-check-sqlalchemy`.

## Test plan

### Unit test

Add a focused test for the database health probe.

The test should:

- provide a mocked database session;
- call the health-check database probe;
- verify `db.execute()` receives a SQLAlchemy `TextClause` containing `SELECT 1`;
- verify the probe completes without raising the reported SQLAlchemy textual-SQL error.

Expected result: the new test passes.

### Type checking

Run the relevant mypy check for `api.routes.health`.

Expected result: the module passes without the `call-overload` suppression in `pyproject.toml`.

### Reproduction

Run the supported reproduction setup with `alembic upgrade head` before starting the application.

Check the health-check logs for the reported SQLAlchemy `ArgumentError`.

If the environment still prevents the endpoint from reaching the database probe, record that limitation. Do not use a `503` from `/health` alone as the pass signal because the separate Redis problem in #62 can still cause `/health` to return `503`.

## Risks / Unknowns

- I did not reproduce the SQLAlchemy error in my original environment.
- My original Python 3.14/NumPy 2 environment prevented the full reproduction from reaching the database probe.
- The repository does not currently have a dedicated health-check test, so the plan adds one rather than assuming an existing test.
- The Redis issue in #62 is separate and may continue to make `/health` return `503`.
- I will report any reproduction limitation instead of claiming a result I did not observe.

## Deviations

- The full unit test suite passed: 375 passed, 53 xfailed, 1 deselected.
- The focused health-check test passed and confirms the PostgreSQL probe passes a SQLAlchemy `TextClause` containing `SELECT 1`.
- The relevant mypy check still reports the existing Redis constructor error at `api/routes/health.py:47`. This is unrelated to the PostgreSQL fix and corresponds to the separate Redis issue in #62, so I did not change it.
- `alembic upgrade head` could not run because PostgreSQL was not reachable at `localhost:5433`. Because the migration could not be applied and the application was not running, I could not complete the live `/health` reproduction after the change.
- `curl -i http://localhost:8000/health` therefore could not connect to the application.