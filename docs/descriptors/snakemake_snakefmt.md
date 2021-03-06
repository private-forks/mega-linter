<!-- markdownlint-disable MD033 MD041 -->
<!-- Generated by .automation/build.py, please do not update manually -->
# snakefmt

## snakefmt documentation

- Version in Mega-Linter: **0.2.4**
- Visit [Official Web Site](https://github.com/snakemake/snakefmt#readme){target=_blank}
- See [How to configure snakefmt rules](https://github.com/snakemake/snakefmt#configuration){target=_blank}
  - If custom .snakefmt.toml is not found, [.snakefmt.toml](https://github.com/nvuillam/mega-linter/tree/master/TEMPLATES/.snakefmt.toml){target=_blank} will be used

[![snakefmt - GitHub](https://gh-card.dev/repos/snakemake/snakefmt.svg?fullname=)](https://github.com/snakemake/snakefmt){target=_blank}

## Configuration in Mega-Linter

- Enable snakefmt by adding `SNAKEMAKE_SNAKEFMT` in [ENABLE_LINTERS variable](/configuration/#activation-and-deactivation)
- Disable snakefmt by adding `SNAKEMAKE_SNAKEFMT` in [DISABLE_LINTERS variable](/configuration/#activation-and-deactivation)

- Enable **auto-fixes** by adding `SNAKEMAKE_SNAKEFMT` in [APPLY_FIXES variable](/configuration/#apply-fixes)

| Variable | Description | Default value |
| ----------------- | -------------- | -------------- |
| SNAKEMAKE_SNAKEFMT_ARGUMENTS | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"` |  |
| SNAKEMAKE_SNAKEFMT_FILTER_REGEX_INCLUDE | Custom regex including filter<br/>Ex: `\/(src\|lib)\/` | Include every file |
| SNAKEMAKE_SNAKEFMT_FILTER_REGEX_EXCLUDE | Custom regex excluding filter<br/>Ex: `\/(test\|examples)\/` | Exclude no file |
| SNAKEMAKE_SNAKEFMT_FILE_NAME | snakefmt configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it | `.snakefmt.toml` |
| SNAKEMAKE_SNAKEFMT_RULES_PATH | Path where to find linter configuration file | Workspace folder, then Mega-Linter default rules |
| SNAKEMAKE_SNAKEFMT_DISABLE_ERRORS | Run linter but disable crash if errors found | `false` |

## Behind the scenes

### How are identified applicable files

- File extensions:
  - `.smk`

- File names:
  - `Snakefile`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->

### Example calls

```shell
snakefmt --check --compact-diff Snakefile
```

```shell
snakefmt --check --compact-diff --config .snakefmt.toml Snakefile
```

```shell
snakefmt --config .snakefmt.toml Snakefile
```


### Help content

```shell
Usage: snakefmt [OPTIONS] [SRC]...

  The uncompromising Snakemake code formatter.

  SRC specifies directories and files to format. Directories will be
  searched for file names that conform to the include/exclude patterns
  provided.

  Files are modified in-place by default; use diff, check, or  `snakefmt - <
  Snakefile` to avoid this.

Options:
  -l, --line-length INT  Lines longer than INT will be wrapped. [default: 88]
  --check                Don't write the files back, just return the status.
                         Return code 0 means nothing would change. Return code
                         1 means some files would be reformatted. Return code
                         123 means there was an error.

  -d, --diff             Don't write the files back, just output a diff for
                         each file to stdout.

  --compact-diff         Same as --diff but only shows lines that would change
                         plus a few lines of context.

  --include PATTERN      A regular expression that matches files and
                         directories that should be included on recursive
                         searches.  An empty value means all files are
                         included regardless of the name.  Use forward slashes
                         for directories on all platforms (Windows, too).
                         Exclusions are calculated first, inclusions later.
                         [default: (\.smk$|^Snakefile)]

  --exclude PATTERN      A regular expression that matches files and
                         directories that should be excluded on recursive
                         searches.  An empty value means no paths are
                         excluded. Use forward slashes for directories on all
                         platforms (Windows, too). Exclusions are calculated
                         first, inclusions later.  [default: (\.snakemake|\.eg
                         gs|\.git|\.hg|\.mypy_cache|\.nox|\.tox|\.venv|\.svn|_
                         build|buck-out|build|dist)]

  -c, --config PATH      Read configuration from PATH. By default, will try to
                         read from `./pyproject.toml`

  -h, --help             Show this message and exit.
  -V, --version          Show the version and exit.
  -v, --verbose          Turns on debug-level logging.
```

### Installation on mega-linter Docker image

- PIP packages (Python):
  - [snakefmt](https://pypi.org/project/snakefmt)

### Example success log

```shell
Results of snakefmt linter (version 0.2.4)
See documentation on https://nvuillam.github.io/mega-linter/descriptors/snakemake_snakefmt/
-----------------------------------------------

[SUCCESS] .automation/test/snakemake/snakemake_good_1.smk
    =====> Diff for .automation/test/snakemake/snakemake_good_1.smk <=====
    
    
    [INFO] All 1 file(s) would be left unchanged 🎉

```

### Example error log

```shell
Results of snakefmt linter (version 0.2.4)
See documentation on https://nvuillam.github.io/mega-linter/descriptors/snakemake_snakefmt/
-----------------------------------------------

[ERROR] .automation/test/snakemake/snakemake_bad_1.smk
    =====> Diff for .automation/test/snakemake/snakemake_bad_1.smk <=====
    
    --- original
    +++ new
    @@ -1,10 +1,11 @@
     rule all:
         input:
    -        file1='result.txt',
    +        file1="result.txt",
    +
     
     rule simulation:
         output:
    -        file1="result.txt"
    +        file1="result.txt",
         shell:
             """
             touch {output}
    
    [INFO] 1 file(s) would be changed 😬

```
