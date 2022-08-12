# Sentinel

Sentinel is an application written in Python that may be used to perform sentiment analysis on a piece of text. It leverages an external API for this purpose and provides a safe default when the API is unavailable.

## Code Workflow
----------------

1. Create new-branch for code
1. Add code to new-branch
1. Create PR from new-branch to develop -> triggers tests
1. Merge PR into develop (tests must be passing) -> triggers deploy to dev
1. Create PR from develop to main -> triggers tests
1. Merge PR into main (tests must be passing) -> triggers deploy to prd


### Dependencies
- [poetry](https://github.com/abatilo/actions-poetry)
- [python](https://github.com/actions/setup-python)
- [deploy to heroku](https://github.com/marketplace/actions/deploy-to-heroku)


### Creating new environment
~~~ bash
heroku create --app=<app-name>
heroku buildpacks:clear --app=<app-name>
heroku buildpacks:add https://github.com/moneymeets/python-poetry-buildpack.git --app=<app-name>
heroku buildpacks:add heroku/python --app=<app-name>
~~~


## Commands
-----------

The following commands describe how the application may be built, run and tested. Note that [Python 3.10](https://docs.python.org/3/whatsnew/3.10.html) and [Poetry](https://python-poetry.org/) are required.

**Setup**

```sh
poetry install
```

**Run**

```sh
uvicorn sentinel.api:app --host 0.0.0.0 --port 8000 --reload
```

From another terminal window, you may query the application with:

```sh
curl -XPOST http://localhost:8000/analyze -H "Content-Type: application/json" -d '{"text": "This is a test."}'
```

**Unit tests and coverage**

```sh
poetry run coverage run -m pytest tests/test_unit.py
poetry run coverage report --fail-under 90
```

**Regression tests**

By default, regression tests run against an application running on `localhost:8000`. However, you may use the `BASE_URL` environment variable to run against a different URL.

```sh
BASE_URL=http://localhost:8000 poetry run pytest tests/test_regression.py
```

**Integration tests**

```sh
poetry run pytest tests/test_integration.py
```
