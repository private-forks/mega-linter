<!-- markdownlint-disable MD033 MD041 -->
<!-- Generated by .automation/build.py, please do not update manually -->
# rstfmt

## rstfmt documentation

- Visit [Official Web Site](https://github.com/dzhu/rstfmt#readme){target=_blank}

[![rstfmt - GitHub](https://gh-card.dev/repos/dzhu/rstfmt.svg?fullname=)](https://github.com/dzhu/rstfmt){target=_blank}

## Configuration in Mega-Linter

- Enable rstfmt by adding `RST_RSTFMT` in [ENABLE_LINTERS variable](/configuration/#activation-and-deactivation)
- Disable rstfmt by adding `RST_RSTFMT` in [DISABLE_LINTERS variable](/configuration/#activation-and-deactivation)

- Enable **auto-fixes** by adding `RST_RSTFMT` in [APPLY_FIXES variable](/configuration/#apply-fixes)

| Variable | Description | Default value |
| ----------------- | -------------- | -------------- |
| RST_RSTFMT_ARGUMENTS | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"` |  |
| RST_RSTFMT_FILTER_REGEX_INCLUDE | Custom regex including filter<br/>Ex: `\/(src\|lib)\/` | Include every file |
| RST_RSTFMT_FILTER_REGEX_EXCLUDE | Custom regex excluding filter<br/>Ex: `\/(test\|examples)\/` | Exclude no file |
| RST_RSTFMT_DISABLE_ERRORS | Run linter but disable crash if errors found | `false` |

## Behind the scenes

### How are identified applicable files

- File extensions:
  - `.rst`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->

### Example calls

```shell
rstfmt myfile.rst
```

```shell
rstfmt -i myfile.rst
```


### Help content

```shell
usage: rstfmt [-h] [-v] [-w WIDTH] [--check] [--test] [files ...]

positional arguments:
  files

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose
  -w WIDTH, --width WIDTH
  --check
  --test
```

### Installation on mega-linter Docker image

- PIP packages (Python):
  - [rstfmt](https://pypi.org/project/rstfmt)
