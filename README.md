 # realitycheck
A sample app that reality checks some basic features on your installation of CircleCI:
1. Runs all known `resource_class` options (*NOTE:* your build instances must be large enough to accomodate these options)
2. Runs `machine` executor & `setup_remote_docker` builds, both with and without [Docker Layer Caching](https://circleci.com/docs/2.0/docker-layer-caching)
3. Read/write workspaces
4. Tests that the `org-global` context is working (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in the `org-global` context)
5. Tests writing artifacts

To test your installation, fork this repository and start building it on your installation of CircleCI.

If you have more ideas for things that should tested, please submit a PR against the open-source repository on GitHub where this project is maintained: <https://github.com/circleci/realitycheck>

See the current CI status of the main repo at <https://circleci.com/gh/circleci/workflows/realitycheck>.

View the LICENSE file in this repository for licensing information.
