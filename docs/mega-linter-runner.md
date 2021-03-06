<!-- markdownlint-disable MD013 MD033 MD041 -->

# Mega-Linter Runner
<!-- readme-header-start-->

<!-- readme-header-end-->

This package allows to run [Mega-Linter](https://nvuillam.github.io/mega-linter/) locally before running it in your CD/CI workflow, or simply to locally apply reformatting and fixes without having to install up to date linters for your files

## Installation

### Pre-requisites

You need to have [NodeJS](https://nodejs.org/en/) and [Docker](https://www.docker.com/) installed on your computer to run Mega-Linter locally with Mega-Linter Runner

### Global installation

```shell
npm install mega-linter-runner -g
```

### Local installation

```shell
npm install mega-linter-runner --save-dev
```

### No installation

You can run mega-linter-runner without installation by using `npx`

Example:

```shell
npx mega-linter-runner -r insiders -e 'ENABLE=MARKDOWN,YAML' -e 'SHOW_ELAPSED_TIME=true'
```

## Usage

```shell
mega-linter-runner [OPTIONS]
```

The options are only related to mega-linter-runner. For Mega-Linter options, please use a `.mega-linter.yml` [configuration file](#configuration)

| Option             | Description                                               |
|--------------------|-----------------------------------------------------------|
| `-p` `--path`      | Directory containing the files to lint (default: current directory)    |
| `-e` `--env`      | Environment variables for Mega-Linter, following format **'ENV_VAR_NAME=VALUE'** (Warning: Quotes are mandatory)    |
| `--fix`            | Automatically apply formatting and fixes in your files    |
| `-r` `--release`    | Allows to override Mega-Linter version used (default: v4 stable)  |
| `-h` `--help`      | Show mega-linter-runner help    |
| `-v` `--version`   | Show mega-linter-runner version    |

_You can also use `npx mega-linter-runner` if you do not want to install the package_

### Examples

```shell
mega-linter-runner
```

```shell
mega-linter-runner -p myFolder --fix
```

```shell
mega-linter-runner -r insiders -e 'ENABLE=MARKDOWN,YAML' -e 'SHOW_ELAPSED_TIME=true'
```

## Configuration

Default configuration is ready out of the box

You can define a [.mega-linter.yml](https://nvuillam.github.io/mega-linter/#configuration) configuration file at the root of your repository to customize or deactivate the included linters
<!-- linters-section-start -->

<!-- linters-section-end -->
