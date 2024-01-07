# Hobbython

This repository is a monorepo that contains python hobby projects.

## Setup

This repository leverages [Poetry](https://python-poetry.org/) for efficient dependency management. To ensure a smooth setup, please ensure Poetry is installed on your system. You can find the installation guide [here](https://python-poetry.org/docs/#installing-with-pipx).

## Key Concepts

- Dependencies are managed using a `pyproject.toml` file in each directory.
- Common code is packaged in the `shared` directory and referenced in each project.
- Common code is referenced using relative paths, and it's not packaged as a wheel.
- Development environment setup and deployment image building processes are managed using a Makefile and a Dockerfile.
- Local package dependencies are handled without the use of scripts as much as possible. Instead, those processes are described in the Makefile and Dockerfile.


## Directory Structure

Here's a breakdown of the top-level items in our directory structure:

- `projects`: This directory houses each individual project. 
- `shared`: This is where the common code shared across multiple projects is located.
- `pyproject.toml`: This is the root configuration file where development tools like linters and formatters such as Flake8 and Black are specified.

The structure is as follows:

```
python-monorepo
├── .flake8
├── README.md
├── poetry.lock
├── pyproject.toml
├── projects
│   ├── project-a
│   │   ├── .devcontainer
│   │   │   ├── Dockerfile
│   │   │   └── devcontainer.json
│   │   ├── Dockerfile
│   │   ├── Makefile
│   │   ├── poetry.lock
│   │   ├── pyproject.toml
│   │   ├── run.py
│   │   ├── src
│   │   │   ├── __init__.py
│   │   │   └── pipeline.py
│   │   └── tests
│   │       ├── __init__.py
│   │       └── test_pipeline.py
│   └── project-b
│       ├── src
│       │   └── __init__.py
│       └── tests
│           └── __init__.py
└── shared
    ├── pkg1
    │   ├── __pycache__
    │   ├── pkg1
    │   │   ├── __init__.py
    │   │   └── base_pipeline.py
    │   ├── poetry.lock
    │   └── pyproject.toml
    └── pkg2
        ├── pkg2
        │   ├── __init__.py
        │   └── calc.py
        ├── poetry.lock
        └── pyproject.toml
```

## Adding Local Packages

To add local packages to your project, add them to the `pyproject.toml` file:

```bash
cd projects/project-xxx
poetry add ../../shared/pkg-yyy/
```

Add the copied shared package to the Makefile:

```bash
# Copy the shared package written in pyproject.toml
cp -r ../../shared/pkg-yyy $(TMP_DIR)/pkg-yyy
```

And also add the package to the Dockerfile:

```bash
# Copy the shared package written in pyproject.toml
COPY ./pkg-yyy/ /shared/pkg-yyy/
```

## How to Use

### Development

For setting up a development environment, navigate to the desired project directory and run `poetry install`.

```bash
cd projects/project-xxx
poetry install
poetry run python main_python_file.py
```
