# Description
Useful template for Machine Learning development using python in docker container.
By using this template, you can skip troublesome initial settings of project.
This template contain the following setting.
- Two dockerfile for ML development
    - First is base dockerfile for build base docker image in .devcontainer/base/
        - Define python and CUDA version through environment variable
        - Set UID and GID through environment variable so that directly mount work expectedly
        - Contain basic dependencies python developing
    - Second is dockerfile which run container for specific use case in .devcontainer/
        - Install python packages used in project according to .devcontainer/requirements.txt
        - Execute .devcontainer/setup.sh for some specific settings
- Docker compose file for each docker file
    - Define docker build setting which include environment variable declare in .env
    - Define mount setting of workspace and ssh setting, etc
    - enable using GPU in docker container
- .devcontainer setting for run container using dev container extension of VScode
    - define which VScode extension to install in container
- VScode setting for python development
    - Auto format by black
    - Import organization by isort
    - Linting python file by flake8
    - Type check by mypy
    - Linting dockerfile by hadolint
- Pre-commit setting for check commit appropriateness
    - Auto file formatting
    - Check by linter
# Requirements
- Docker environment
- Pre-commit package(You can install it by `pip3 install pre-commit`)
- VScode dev container extension

# How to use
1. Set environment variable in .env file
1. Build base docker image`cd ./.devcontainer/base && docker compose --env-file ../../.env build`
1. Define necessary python packages in .devcontainer/requirements.txt
1. Build docker image`cd ./.devcontainer && docker compose --env-file ../.env build`
1. Launch container and connect to it using dev container

Of course, you can modify any setting in this repository for your preference
