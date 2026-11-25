# ws Python project copier template

A [copier](https://copier.readthedocs.io/) template for a new Python project.

The new project has:
- uv for the environment and dependencies, with the Python version pinned in `.python-version`
- pre-commit hooks that run Ruff formatting and linting, plus checks for whitespace, line endings, and large files
- Ruff settings in `pyproject.toml`
- a direnv `.envrc` that activates the project environment when a shell enters the directory
- a `.gitignore` for environments, build output, notebooks, and data files
- a minimal `README.md` and `script.py`

requirements: `uv` and `git`, and optionally `direnv` on macOS and Linux. Copier runs through `uvx`, so it needs no installation, and `uv sync` installs the pinned Python version if it's missing.


## copier questions

- project name: defaults to the directory name
- Python version: defaults to 3.13

To skip the questions, for example when an agent runs the command, add `--defaults`. Pass any answer that differs from its default with `--data`. For example, the first line of the command chains below becomes:
```bash
uvx copier copy --defaults --data python_version=3.12 https://github.com/williamstarkbio/python-project-template "$NEW_PROJECT_DIR"
```

Run each command chain below as a single command, since an activated environment doesn't carry over to a separate shell.


## Linux and macOS

save the project path:
```bash
NEW_PROJECT_DIR=<new_project_directory>
```

create the project, commit it, install the dependencies, and install the pre-commit hooks:
```bash
uvx copier copy https://github.com/williamstarkbio/python-project-template "$NEW_PROJECT_DIR" && \
cd "$NEW_PROJECT_DIR" && \
git init --initial-branch main && \
git add . && \
git commit -m "project created from github.com/williamstarkbio/python-project-template" && \
uv sync && \
git add uv.lock && \
git commit -m "install dependencies" && \
source .venv/bin/activate && \
pre-commit install
```

with direnv, activate the environment automatically whenever a shell enters the project directory:
```bash
direnv allow
```


## Windows

### Command Prompt (cmd)

save the project path:
```cmd
set NEW_PROJECT_DIR=<new_project_directory>
```

create the project, commit it, install the dependencies, and install the pre-commit hooks:
```cmd
uvx copier copy https://github.com/williamstarkbio/python-project-template "%NEW_PROJECT_DIR%" && ^
cd /d "%NEW_PROJECT_DIR%" && ^
git init --initial-branch main && ^
git add . && ^
git commit -m "project created from github.com/williamstarkbio/python-project-template" && ^
uv sync && ^
git add uv.lock && ^
git commit -m "install dependencies" && ^
call .venv\Scripts\activate.bat && ^
pre-commit install
```

### PowerShell

allow local scripts, such as the environment's activation script, once per account:
```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

save the project path:
```powershell
$NEW_PROJECT_DIR="<new_project_directory>"
```

create the project, commit it, install the dependencies, and install the pre-commit hooks:
```powershell
uvx copier copy https://github.com/williamstarkbio/python-project-template "$NEW_PROJECT_DIR";
cd "$NEW_PROJECT_DIR";
git init --initial-branch main;
git add .;
git commit -m "project created from github.com/williamstarkbio/python-project-template";
uv sync;
git add uv.lock;
git commit -m "install dependencies";
.\.venv\Scripts\Activate.ps1;
pre-commit install;
ls
```
