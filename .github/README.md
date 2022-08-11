## Workflow
1. Create new branch for code, new-branch
1. Add code to new-branch
1. Create PR from new-branch to main -> triggers build, then test
1. Merge PR into main (check from test step must pass to merge) -> triggers deploy


## Dependencies
- [poetry](https://github.com/abatilo/actions-poetry)
- [python](https://github.com/actions/setup-python)
