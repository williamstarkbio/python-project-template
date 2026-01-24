# ws Python project copier template

create a new project using the template:

save the project desired path:
```bash
NEW_PROJECT_DIR=<new_project_directory>
```

create the project:
```bash
uvx copier copy https://github.com/williamstarkbio/python-project-template "$NEW_PROJECT_DIR" && \
cd "$NEW_PROJECT_DIR" && \
git init --initial-branch main && \
git add . && \
git commit -m "project created from github.com/williamstarkbio/python-project-template" && \
uv sync && \
git add uv.lock && \
git commit -m "install dependencies" && \
direnv allow && \
source .venv/bin/activate && \
pre-commit install
```

**features**:
- uv for dependencies management
- pre-commit to automate formatting and linting with Ruff
- direnv `.envrc` to automatically load the project virtual environment


## use the project template on Windows

### in Command Prompt (cmd)

save the project desired path:
```cmd
set NEW_PROJECT_DIR=<new_project_directory>
```

create the project:
```cmd
uvx copier copy https://github.com/williamstarkbio/python-project-template "%NEW_PROJECT_DIR%" && ^
cd "%NEW_PROJECT_DIR%" && ^
git init --initial-branch main && ^
git add . && ^
git commit -m "project created from github.com/williamstarkbio/python-project-template" && ^
uv sync && ^
git add uv.lock && ^
git commit -m "install dependencies" && ^
.venv\Scripts\activate.bat && ^
pre-commit install
```

### in PowerShell

save the project desired path:
```powershell
$NEW_PROJECT_DIR="<new_project_directory>"
```

create the project:
```powershell
uvx copier copy https://github.com/williamstarkbio/python-project-template "$NEW_PROJECT_DIR";
cd "$NEW_PROJECT_DIR";
git init --initial-branch main;
git add .;
git commit -m "project created from github.com/williamstarkbio/python-project-template";
uv sync;
git add uv.lock;
git commit -m "install dependencies";
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned;
.\.venv\Scripts\Activate.ps1;
pre-commit install;
ls
```
