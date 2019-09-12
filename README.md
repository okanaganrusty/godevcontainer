# Go Dev Container

*Golang development container for Visual Studio Code Remote Containers Development*

[![godevcontainer](https://github.com/qdm12/godevcontainer/raw/master/title.png)](https://hub.docker.com/r/qmcgaw/godevcontainer)

[![Docker Build Status](https://img.shields.io/docker/cloud/build/qmcgaw/godevcontainer.svg)](https://hub.docker.com/r/qmcgaw/godevcontainer)

[![GitHub last commit](https://img.shields.io/github/last-commit/qdm12/godevcontainer.svg)](https://github.com/qdm12/godevcontainer/issues)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/y/qdm12/godevcontainer.svg)](https://github.com/qdm12/godevcontainer/issues)
[![GitHub issues](https://img.shields.io/github/issues/qdm12/godevcontainer.svg)](https://github.com/qdm12/godevcontainer/issues)

[![Docker Pulls](https://img.shields.io/docker/pulls/qmcgaw/godevcontainer.svg)](https://hub.docker.com/r/qmcgaw/godevcontainer)
[![Docker Stars](https://img.shields.io/docker/stars/qmcgaw/godevcontainer.svg)](https://hub.docker.com/r/qmcgaw/godevcontainer)
[![Docker Automated](https://img.shields.io/docker/cloud/automated/qmcgaw/godevcontainer.svg)](https://hub.docker.com/r/qmcgaw/godevcontainer)

[![Image size](https://images.microbadger.com/badges/image/qmcgaw/godevcontainer.svg)](https://microbadger.com/images/qmcgaw/godevcontainer)
[![Image version](https://images.microbadger.com/badges/version/qmcgaw/godevcontainer.svg)](https://microbadger.com/images/qmcgaw/godevcontainer)

[![Donate PayPal](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/qdm12)

| Image size |
| --- |
| 445MB |

This is to be used with Visual Studio Code Remote Containers development.

In a new project:

1. Create a directory `.devcontainer`
1. Create a Dockerfile `.devcontainer/Dockerfile` with:

    ```Dockerfile
    FROM qmcgaw/godevcontainer
    ```

    This will automatically download the image from Docker Hub.
    You can also build it yourself with

    ```sh
    docker build -t qmcgaw/godevcontainer https://github.com/qdm12/godevcontainer.git
    ```

1. Create `.devcontainer/devcontainer.json` with:

    ```json
    {
        "name": "Your project Dev",
        "dockerFile": "Dockerfile",
        // "appPort": 8000,
        "extensions": [
            "ms-vscode.go",
            // "softwaredotcom.swdc-vscode",
            "davidanson.vscode-markdownlint",
            "shardulm94.trailing-spaces",
            "IBM.output-colorizer"
        ],
        "settings": {
            "go.useLanguageServer": true
        },
        "postCreateCommand": "go mod download",
        "runArgs": [
            "-u",
            "vscode",
            "--cap-add=SYS_PTRACE",
            "--security-opt",
            "seccomp=unconfined",
            // Linux
            "-v", "$HOME/.ssh:/home/vscode/.ssh:ro",
            // Windows
            // "v", "${env:HOME}/.ssh:/home/vscode/.ssh:ro"
        ]
    }
    ```

1. Open the command palette in Visual Studio Code and select `Remote-Containers: Open Folder in Container...` and
choose your project directory

## TODOs

## License

This repository is under an [MIT license](https://github.com/qdm12/godevcontainer/master/LICENSE)