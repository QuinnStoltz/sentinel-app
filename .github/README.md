## Workflow
1. Create new branch for code
1. Add code -> each commit triggers linting action?
1. Create PR against main -> triggers build, then test, then deploy dev
1. Merge PR into main (requires check from previous step to pass) -> triggers build, then deploy to prd


## Dependencies
- [poetry](https://github.com/abatilo/actions-poetry)
- [python](https://github.com/actions/setup-python)

