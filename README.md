# workflows
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
re-usable workflows

## dev workflow
The [dev workflow](.github/workflows/dev.yml) does the following:
- build the docker image
- deploy to dev via gitops

A docker image is build and pushed to our docker registry in AWS by a github workflow. It is triggered by each new PR merged into main.
Furthermore, after the docker build on the main branch, the kubernetes deployment files for the develop environment are patched with the newly created image. Like this, the image is automatically deployed.

## staging workflow
The [staging workflow](.github/workflows/staging.yml) does the following:
It is triggered on git tags, re-tags the latest docker image and patches kubernetes deployment files for the staging environment.
