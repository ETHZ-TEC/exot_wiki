# Code style

The project uses code formatting tools to make the code style consistent and readable. It's recommended that the following tools are used in the Python-based *Data Processing* repository and the C++ based repositories.

## Data processing

Formatting Python source code is done with the help of two tools: [Black](https://black.readthedocs.io/en/stable/index.html) and [isort](https://pypi.org/project/isort/). These dependencies are defined in the Poetry's *[pyproject.toml](https://gitlab.ethz.ch/tec/research/exot/datapro/blob/develop/pyproject.toml)* file at the root of the repository. To have them available in the Python environment, make sure to pass the option `--dev` to install development dependencies when bootstrapping with `poetry install`.

The first tool, [Black](https://black.readthedocs.io/en/stable/index.html), enforces a consistent source code formatting style and relieves the user of manual effort. The settings for the formatter are defined in the *[pyproject.toml](https://gitlab.ethz.ch/tec/research/exot/datapro/blob/develop/pyproject.toml)* file:

```toml
[tool.black]
line-length = 96
target_version = ['py37']
include = '\.pyi?$'
```

To format a file or a directory (recursively) use the following command:

```bash
poetry run black --config ./pyproject.toml <file/directory>
```

The second tool, [isort](https://pypi.org/project/isort/), makes sure that the imports are sorted and deduplicated in all Python source files. All imports are sorted alphabetically and grouped into three categories: 1) Python's standard library; 2) third-party libraries; 3) local imports. The sorting and formatting settings are defined in the *[setup.cfg](https://gitlab.ethz.ch/tec/research/exot/datapro/blob/develop/setup.cfg)* file at the root of the repository.

```toml
[isort]
line_length = 96
multi_line_output = 3
balanced_wrapping = true
use_parentheses = true
combine_star = true
```

To format all source files (in place) use the following command (at the root of the repository):

```bash
poetry run isort -sp ./setup.cfg -y
```

## C++ applications and the application library

The C++ source code files should be processed with the [clang-format](https://clang.llvm.org/docs/ClangFormat.html) utility. The formatter is based on LLVM and excels at producing consistent and nicely formatter source code. Its settings are defined in the *[.clang-format](https://gitlab.ethz.ch/tec/research/exot/app_lib/blob/develop/.clang-format)* file at the root of the Application Library repository.

```
---
BasedOnStyle: Google
IndentWidth: 2
ColumnLimit: 80
AlignConsecutiveAssignments: true
AlignConsecutiveDeclarations: false
AlignEscapedNewlines: true
AllowShortBlocksOnASingleLine: true
AllowShortFunctionsOnASingleLine: InlineOnly
DerivePointerAlignment: false
PointerAlignment: Left
SortUsingDeclarations: true
---
```

Make sure that this config file is accessible in the current working directory or any parent directory before running the tool. To perform the formatting in place on a file, run the following command:

```bash
clang-format -i -style=file <path/to/file(s)>
```

For example, run `clang-format -i -style=file {include,src}/**.{h,cpp}` to format all files in the *include* and *src* directories.

The formatter is also available in the Docker environment. If you have it configured, prepend `dock ` to the commands above, for example `dock clang-format -i -style=file include/**.h`.