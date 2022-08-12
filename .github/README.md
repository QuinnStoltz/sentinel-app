## Workflow
1. Create new branch for code
1. Add code to new-branch
1. Create PR from new-branch to develop -> triggers build, then test
1. Merge PR into develop (check from test step must pass to merge) -> triggers deploy to dev
1. Create PR from develop to main -> triggers build, then test
1. Merge PR into main (check from test step must pass to merge) -> triggers deploy to prd


## Dependencies
- [poetry](https://github.com/abatilo/actions-poetry)
- [python](https://github.com/actions/setup-python)
- [deploy to heroku](https://github.com/marketplace/actions/deploy-to-heroku)


## Creating new environment
~~~ bash
heroku create --remote [dev|prd]
heroku buildpacks:clear --remote [dev|prd]
heroku buildpacks:add https://github.com/moneymeets/python-poetry-buildpack.git --remote [dev|prd]
heroku buildpacks:add heroku/python --remote [dev|prd]
~~~
