# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

DiveshIO

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/61#issuecomment-6030341135

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

## Your branch

**Branch**

fix/61-health-check-sqlalchemy

**Evidence**

### Before

I reproduced the issue on commit `f89c06f`.

I started the services with:

```text
docker compose up -d
```

Then checked the health endpoint with:

```text
curl -i http://localhost:8000/health
```

The endpoint returned:

```text
HTTP/1.1 503 Service Unavailable
```

with PostgreSQL and Redis unhealthy and the vector database healthy.

The PostgreSQL logs showed:

```text
FATAL: database "pathreview" does not exist
```

The vector database also failed because NumPy 2.0 removed `np.float_`.

The health-check code at the time contained:

```python
await db.execute("SELECT 1")
```

I could not reproduce the specific SQLAlchemy `ArgumentError` because my environment failed before reaching the database health-check query.

### After

I changed the PostgreSQL health check to:

```python
await db.execute(text("SELECT 1"))
```

and imported `text` from SQLAlchemy.

I also added a focused test that checks that `db.execute()` receives a SQLAlchemy `TextClause` containing `SELECT 1`.

The full unit test suite passed:

```text
375 passed, 53 xfailed, 1 deselected
```

The pre-commit checks on the committed changes also passed:

```text
ruff...Passed
black...Passed
mypy...Passed
```

I also ran `git diff --check` and it returned no errors.

The full `make typecheck` still reports the existing Redis constructor error at `api/routes/health.py:47`. This is related to the separate Redis issue #62, so I did not change it.

I tried to run the post-change reproduction with:

```text
alembic upgrade head
```

but PostgreSQL was not reachable at `localhost:5433`:

```text
OSError: Multiple exceptions: [Errno 61] Connect call failed ('::1', 5433), [Errno 61] Connect call failed ('127.0.0.1', 5433)
```

Because the migration could not run and the application was not running, the final health endpoint check could not be completed:

```text
curl -i http://localhost:8000/health
curl: (7) Failed to connect to localhost port 8000 after 0 ms: Couldn't connect to server
```

## Eval iterations

**Run history**

The final eval run had:

```text
agreement: 19/20 scored items  (bar: 18/20: PASS)
```

This was the final run saved to `eval-run.txt`.

**Package analysis**

I picked `pkg-14`.

The eval output was:

```text
pkg-14  clear-accept  accept  reject  NO  failed: diagnosis, cause, execution, honesty
```

The gold label was `accept`, but the rubric returned `reject`. This was the only package where the rubric disagreed with the gold label. The other 19 scored packages agreed, giving an overall agreement of 19/20.

**Check rationale**

One check from my `rubric.md` is:

> The planned fix works on the cause shown by the evidence and is not only hiding the problem. If the cause is not fully known, the plan says what needs to be checked.

I kept this check because I did not personally reproduce the SQLAlchemy error. The plan needs to separate what I actually saw from what the issue and code show. The plan therefore does not claim that my environment reproduced the error and explains what still needs to be checked during the build.

**Trade-offs**

I kept the rubric strict about evidence instead of making it easier for a plan to pass by claiming something was reproduced when it was not. This means a plan can be rejected when the cause is not supported by the evidence, even if the proposed fix sounds reasonable.

For this run, the rubric still passed the required threshold with 19/20 agreement, so I did not change the checks after the final run.