### project structure

This repo is a proof-of-concept model for predicting IMDB ratings of a movie.

This README is mainly instructions for environment setup using poetry.

For a summary of the modeling process, please see SUMMARY.md. For the actual code used for modeling, please see imdb_ratings/notebooks/
### environment setup

- [install pyenv](https://realpython.com/intro-to-pyenv/)

- install python `3.7.2` (minimum) using pyenv: `pyenv install -v 3.7.2`

- set directory python to project version using pyenv (`^3.7.2`): `pyenv local 3.7.2`

- install poetry
    - `curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python`
    - [docs](https://python-poetry.org/docs/#installation) for other OSs

- clone the repo if you haven't done so yet
    - cd to `parsers` directory
- install poetry dependencies
    - `poetry install`: this should either do a fresh install, or install from the `poetry.lock` file
    - *always* commit the `poetry.lock` if you add or remove a dependencies
    - by default, your package is installed in editable mode and dev dependencies are installed; which is what we want
    - you can now summon your new venv with `poetry shell`
    - to see more info about the venv (such as where it is located): `poetry env info`
        - to get pycharm to recognize it, take the path returned above and append `/bin/python`; enter that when you're in the "Add Interpreter" menu

- install pre-commit hooks
    - in your poetry venv, run `pre-commit install`
    - the hooks will run on commit, but to confirm it is working properly/for funsies, you can run it on all the files: `pre-commit run --all-files`
    - [more on pre-commit hooks](https://pre-commit.com/)

- set up env vars: production (and soon, staging) env vars are stored in K8s and will be loaded when the docker container runs. For local development, you need to use your own env var file.

### testing
- tests run on merge request via gitlab via `.gitlab-ci.yml`

- running tests locally: `pytest tests/`

- for pycharm to recognize your tests, you need to set pytest as your default test runner in `Settings`

### deployment
The output of this repo will be a docker container that will be used to create an Argo pipeline.

Deploy will be handled on merge to the `production` branch via the `.gitlab-ci.yml`.
