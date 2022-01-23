### project structure

This repo is a proof-of-concept model for predicting IMDB ratings of a movie.

This README is mainly instructions for environment setup using poetry.

For a summary of the modeling process, please see SUMMARY.md. 

For the actual code used for modeling, please see `imdb_ratings/notebooks/DataExplorationAndModeling_v1.ipynb`

### environment setup

- [install pyenv](https://realpython.com/intro-to-pyenv/)

- install python `3.7.4` (minimum) using pyenv: `pyenv install -v 3.7.4`

- set directory python to project version using pyenv (`^3.7.4`): `pyenv local 3.7.2`

- install poetry
    - `curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python`
    - [docs](https://python-poetry.org/docs/#installation) for other OSs

- clone the repo if you haven't done so yet
    - cd to repo directory
- install poetry dependencies
    - `poetry install`: this should either do a fresh install, or install from the `poetry.lock` file
    - *always* commit the `poetry.lock` if you add or remove a dependencies
    - by default, your package is installed in editable mode and dev dependencies are installed; which is what we want
    - you can now summon your new venv with `poetry shell`
    - to see more info about the venv (such as where it is located): `poetry env info`
 