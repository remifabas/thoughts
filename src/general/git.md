# Git

## Usefull alias

```
git config --global alias.undo 'reset --soft HEAD^'
git config --global alias.lg "log --color --graph --pretty=format:'%C(#dc322f)%h%C(#b58900)%d %C(#eee8d5)%s %C(#dc322f)| %C(#586f75)%cr %C(#dc322f)| %C(#586e75)%an%Creset' --abbrev-commit"
```

## Gitlab

First you need to create a personal access token
git config --global credential.helper store
git pull

it will ask you your username and password (use your pat). Then there is no need to enter user/password


## Pre-commit

[pre-commit](https://pre-commit.com) is a python tool used to check commit before push

~~~bash
#!/bin/bash

pip3 install pre-commit==3.0.4

pre-commit install
~~~

~~~admonish example title="configuration"

Here is a example of configuration for pre commit, as you can see it use default installed hook and some hook for externals repo

example: commitizen used for git commit angular convention


the file name should be `.pre-commit-config.yaml`

```yaml
# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
default_install_hook_types:
  - pre-commit
  - commit-msg
repos:
  - repo: https://github.com/commitizen-tools/commitizen
    rev: v2.42.1
    hooks:
      - id: commitizen
        stages: [commit-msg]
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: check-json
        stages: [commit]
      - id: check-merge-conflict
        stages: [commit]
      - id: trailing-whitespace
        stages: [commit]
      - id: end-of-file-fixer
        stages: [commit]
      - id: check-yaml
        stages: [commit]
      - id: check-added-large-files
        stages: [commit]
      - id: check-executables-have-shebangs
        stages: [commit]
      - id: detect-aws-credentials
        stages: [commit]
      - id: detect-private-key
        stages: [commit]
  - repo: https://github.com/pre-commit/mirrors-prettier
    # Use the sha or branch you want to point at
    rev: v3.0.0-alpha.6
    hooks:
      - id: prettier
        stages: [commit]
  - repo: https://github.com/shellcheck-py/shellcheck-py
    rev: v0.9.0.2
    hooks:
      - id: shellcheck
        stages: [commit]
  - repo: https://github.com/zricethezav/gitleaks
    rev: v8.16.0
    hooks:
      - id: gitleaks
        stages: [commit]
```

~~~
