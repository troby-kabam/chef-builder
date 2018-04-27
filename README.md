Environments for Chef cookbook development.
This will clone 'sparx-cookbooks' to volumes/.

USE
`env BRANCH=<branch name> make` to clone a target branch.

COMMANDS
`make` OR `make build`
  - This will create the docker image using the local Dockerfile.
  - A different branch can be specified with `env BRANCH=<branch name> make`
`make run`
  - This creates an ephemeral instance of the container and gives you a shell prompt.
`make clean`
  - This removes the image created, and cleans up the cloned repository.

VERSIONS
Chef Development Kit Version: 2.5.3
chef-client version: 13.8.5
delivery version: master (73ebb72a6c42b3d2ff5370c476be800fee7e5427)
berks version: 6.3.1
kitchen version: 1.20.0
inspec version: 1.51.21

CAVEATS
When adding new functionality be sure to add any cleanup steps to `make clean`.
