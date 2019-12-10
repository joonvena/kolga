# Variables

## Overview
An environment variable is a dynamic-named value that can affect the way running processes will
behave on an operating system.

Variables are useful for customizing the CI/CD pipeline as it makes the pipeline more
flexible and easier to configure. It also means less hardcoded values.

## Predefined variables
The DevOps pipeline is build to be able to run existing CI/CD platforms such as GitLab CI,
Travis and CircleCI. It utilizes the variables exposed by those platforms and unifies
them into a set of predefined variables in the DevOps pipeline.

For instance, GitLab exposes a variables named `CI_COMMIT_SHA`. While the name does not
contain anything pointing to GitLab itself, it is uncertain if this variable name is used
on other platforms, for that reason we add a variable `GIT_COMMIT_SHA` which always will
point to the SHA of a commit, no matter the underlying platform, as long as the platform
supplies a predefined variables with the SHA.


| Variable                      | Description                                         | Default                      | CI Support |
|-------------------------------|-----------------------------------------------------|------------------------------|------------|
| CONTAINER\_REGISTRY           | Docker registry URL                                 |                              | GitLab     |
| CONTAINER\_REGISTRY\_PASSWORD | Password for Docker registry                        |                              | GitLab     |
| CONTAINER\_REGISTRY\_REPO     | Docker repository for project                       |                              | Gitlab     |
| CONTAINER\_REGISTRY\_USER     | Username for Docker registry                        |                              | GitLab     |
| DATABASE\_DB                  | Database name for preview environment               | appdb                        |            |
| DATABASE\_PASSWORD            | Database password for preview environment           | UUID value                   |            |
| DATABASE\_USER                | Database user for preview environment               | user                         |            |
| DOCKER\_BUILD\_CONTEXT        | Build context folder                                | .                            |            |
| DOCKER\_BUILD\_SOURCE         | Dockerfile to build from                            | Dockerfile                   |            |
| DOCKER\_HOST                  | Docker runtime                                      | unix:///var/run/docker\.sock |            |
| DOCKER\_IMAGE\_NAME           | Name of docker image \(without tag\)                | PROJECT\_NAME                |            |
| DOCKER\_TEST\_IMAGE\_STAGE    | Which image stage to run tests on                   | development                  |            |
| ENVIRONMENT\_SLUG             | Slug name of CI environment                         |                              | GitLab     |
| ENVIRONMENT\_URL              | Full URL to the upcoming environment                |                              | GitLab     |
| GIT\_COMMIT\_REF\_NAME        | The branch or tag name for which project is built   |                              | GitLab     |
| GIT\_COMMIT\_SHA              | Current commits SHA                                 |                              | GitLab     |
| GIT\_DEFAULT\_TARGET\_BRANCH  | Default branch that is targeted for merges          | master                       | GitLab     |
| GIT\_TARGET\_BRANCH           | Target branch for the specific merge/pull-request   |                              | GitLab     |
| K8S\_INGRESS\_BASE\_DOMAIN    | Kubernetes default base domain for preview          |                              | GitLab     |
| K8S\_NAMESPACE                | Kubernetes namespace to use                         |                              | GitLab     |
| K8S\_SECRET\_PREFIX           | Application environment variable prefix             |                              |            |
| KUBECONFIG                    | Path to Kubernetes config                           |                              |            |
| MYSQL\_ENABLED                | Should a MySQL database be created for preview      | False                        |            |
| MYSQL\_VERSION\_TAG           | Version of MySQL for preview environment            | 9\.6                         |            |
| POSTGRES\_ENABLED             | Should a PostgreSQL database be created for preview | True                         |            |
| POSTGRES\_VERSION\_TAG        | Version of PostgeSQL for preview environment        | 5\.6                         |            |
| PROJECT\_DIR                  | Path to where code is cloned and CI start path      |                              | GitLab     |
| PROJECT\_NAME                 | The name of the project                             |                              | GitLab     |
| PROJECT\_PATH\_SLUG           | Slug to project path \(<org>/<repo>\)               |                              | GitLab     |
| SERVICE\_PORT                 | Port that application listens on                    | 8000                         |            |


## Command variables

Certain variables reflect commands that will be run at certain stages of the applications
life-cycle. Such variables can for instance be used to run a command before the application
starts to do database migrations.


| Variable                      | Description                                         | Default                      | CI Support |
|-------------------------------|-----------------------------------------------------|------------------------------|------------|
| APP\_INITIALIZE\_COMMAND      | Command to run on first start                       |                              |            |
| APP\_MIGRATE\_COMMAND         | Command to run on every update                      |                              |            |
