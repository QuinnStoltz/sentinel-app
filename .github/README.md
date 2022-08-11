## Workflow
1. Create new branch for code, new-branch
1. Add code to new-branch
1. Create PR from new-branch to main -> triggers build, then test
1. Merge PR into main (check from test step must pass to merge) -> triggers deploy


## Dependencies
- [poetry](https://github.com/abatilo/actions-poetry)
- [python](https://github.com/actions/setup-python)
- [deploy to heroku](https://github.com/marketplace/actions/deploy-to-heroku)


## Creating new environment
~~~ bash
heroku create -a <unique-env-name>
heroku buildpacks:clear -a <unique-env-name>
heroku buildpacks:add https://github.com/moneymeets/python-poetry-buildpack.git -a <unique-env-name>
heroku buildpacks:add heroku/python -a <unique-env-name>

heroku create -a sentinel-dev-45684
...

heroku create -a sentinel-prd-98357
...
~~~
