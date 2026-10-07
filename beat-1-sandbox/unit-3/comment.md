I plan to fix issue #61 by updating the PostgreSQL health check in `api/routes/health.py`.

In my own reproduction on `f89c06f`, I did not reach the reported SQLAlchemy error. My environment stopped earlier with PostgreSQL reporting `database "pathreview" does not exist` and the vector database failing because `np.float_` was removed in NumPy 2.0. Other reproductions in this issue reached the reported health-check failure, so I will use the code and test behavior to verify the fix rather than claim that I personally reproduced it.

### Plan

- Change `api/routes/health.py:32` from `await db.execute("SELECT 1")` to `await db.execute(text("SELECT 1"))`.
- Import `text` from SQLAlchemy.
- Add a focused unit test for the database health probe because there is currently no dedicated health-check test under `tests/`.
- Have the test verify that the database probe passes a SQLAlchemy `TextClause` containing `SELECT 1` to `db.execute()`.
- Remove the `api.routes.health` `call-overload` suppression from `pyproject.toml`.
- Run the new focused test and the relevant mypy check.
- Run the available reproduction setup with `alembic upgrade head` and record any environment limitations.
- Keep the Redis issue in #62 out of this change. `/health` may still return `503` because of that separate issue.

Branch: `fix/61-health-check-sqlalchemy`
