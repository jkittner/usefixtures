[![ci](https://github.com/jkittner/usefixtures/workflows/ci/badge.svg)](https://github.com/jkittner/usefixtures/actions?query=workflow%3Aci)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/jkittner/usefixtures/main.svg)](https://results.pre-commit.ci/latest/github/jkittner/usefixtures/main)

# usefixtures

A code formatter to rewrite pytest fixtures passed as unused arguments as a `@pytest.mark.usefixtures` decorator

**still work in progress and only a proof of concept**

## Installation

```
pip install git+https://github.com/jkittner/usefixtures/main
```

## usage

```console
usage: usefixtures [-h] [filenames ...]

positional arguments:
  filenames

options:
  -h, --help  show this help message and exit
```

## pre-commit hook

See [pre-commit](https://pre-commit.com) for instructions

Sample `.pre-commit-config.yaml`:

```yaml
- repo: https://github.com/jkittner/usefixtures
  rev: 0.0.0
  hooks:
    - id: usefixtures
```

## rewrite test functions

```diff
-def test_something(capsys, pure_side_effect_fixture):
+@pytest.mark.usefixtures('pure_side_effect_fixture')
+def test_something(capsys):
     out, err = capsys.readouterr()
```
