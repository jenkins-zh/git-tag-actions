# Git tag Action

GitHub Action for tag your git repository.

## Create Deploy Key

1. Generate deploy key `ssh-keygen -t rsa -f git-backup -q -N ""`
2. Then go to "Settings > Deploy Keys" of the target repository
3. Add your public key within "Allow write access" option.
4. Copy your private deploy key to `GIT_DEPLOY_KEY` secret in your source git repository of "Settings > Secrets"

## Environment Variables

- `GIT_DEPLOY_KEY` - *Required* your deploy key which has **Write access**

```
name: Backup Git Repository

on:
  push:
    branches:
    - master

jobs:
  git-repo-backup:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: git-tag
      uses: jenkins-zh/git-tag-actions@master
      env:
        GIT_DEPLOY_KEY: ${{ secrets.GIT_DEPLOY_KEY }}
```
