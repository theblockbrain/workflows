# workflows
re-usable workflows

Docker image build
A docker image is build and pushed to our docker registry in AWS by a github workflow. It is triggered by each new PR merged into main.

Furthermore, after the docker build on the main branch, the kubernetes deployment files for the develop environment are patched with the newly created image. Like this, the image is automatically deployed.

Another workflow - triggered on git tags - re-tags the latest docker image and patches kubernetes deployment files for the staging environment.

Kubernetes
For the kubernetes deployment, for each environment (develop, staging,...) a subfolder is present in the kubernetes folder. The yaml file located there are monitored by our gitops controller (Argo CD) and deployments / upgrades are done automatically.
