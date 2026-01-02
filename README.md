# ws Python project copier template

create a new project:
```bash
NEW_PROJECT_DIR=<new_project_directory>; \
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

features:
- uv for dependencies management
- pre-commit to automate formatting and linting with Ruff
- direnv `.envrc` to automatically load the project virtual environment
