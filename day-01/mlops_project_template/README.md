```python
markdown_content = """# Day 1 Lab: Poetry Essentials for MLOps

Welcome to Day 1! Today, we are setting up our production Machine Learning environment. We will be using **Poetry** instead of standard `pip` and `requirements.txt` to ensure our dependency management is deterministic, isolated, and reproducible. 

Here are the core commands you need to know to build your MLOps project template.

---

## 1. Creating the Project

When starting fresh, Poetry can scaffold the entire directory structure for you.


```

```text
Created file: poetry_cheatsheet.md

```bash
# Scaffold a brand new project (generates folders, tests, and pyproject.toml)
poetry new mlops_project_template

```

If you have already cloned your Git repository and just want to initialize Poetry inside it:

```bash
# Starts an interactive prompt to create a pyproject.toml in the current folder
poetry init

```

## 2. Managing Dependencies

Poetry prevents the dreaded "it works on my machine" problem by locking versions in a `poetry.lock` file.

```bash
# Install standard packages (updates pyproject.toml and poetry.lock automatically)
poetry add pandas scikit-learn fastapi duckdb

```

You often need tools just for development (like testing or formatting), which shouldn't go into production.

```bash
# Add development-only packages
poetry add pytest black ruff --group dev

```

To replicate an environment (e.g., when you pull a teammate's code from GitHub):

```bash
# Installs exactly what is specified in the poetry.lock file
poetry install

```

To safely remove a package:

```bash
# Uninstalls the package and cleans it out of the configuration files
poetry remove <package_name>

```

## 3. Execution and Environment Management

Poetry handles virtual environments automatically. You don't need to hunt for `venv/Scripts/activate`!

```bash
# Execute a script securely within the isolated Poetry environment
poetry run python data_pipeline.py

```

If you prefer to "activate" the environment and run multiple commands natively in the terminal:

```bash
# Spawns a new shell with the virtual environment activated
poetry shell

```

Need to point VS Code's Python interpreter to your Poetry environment?

```bash
# Displays the path to your virtual environment (copy this path into VS Code)
poetry env info

```

---

## Quick Reference Cheat Sheet

| Command | Action | Use Case in MLOps Pipeline |
| --- | --- | --- |
| `poetry new <name>` | Scaffolds a new project. | Creating the initial boilerplate. |
| `poetry init` | Interactively creates `pyproject.toml`. | Initializing an existing cloned Git repo. |
| `poetry add <pkg>` | Installs a library & updates lock file. | Adding libraries like `fastapi` or `duckdb`. |
| `poetry install` | Installs from `poetry.lock`. | Replicating the environment from GitHub. |
| `poetry update` | Updates dependencies. | Routine maintenance of the ML pipeline. |
| `poetry run <cmd>` | Runs a command in the isolated env. | Executing a training script. |
| `poetry shell` | Activates the virtual env in terminal. | Interactive debugging and development. |
| `poetry check` | Validates `pyproject.toml`. | Pre-commit sanity check before pushing code. |

"""
