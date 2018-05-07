# realitycheck
A sample app that reality-checks some basic features on your installation of CircleCI:
1. Runs jobs using all known `resource_class` options (*NOTE:* your build instances must be large enough to accomodate these options—see our [Configuration Reference](https://circleci.com/docs/2.0/configuration-reference/#resource_class) for details)
2. Runs [machine executor](https://circleci.com/docs/2.0/executor-types/#using-machine) & [remote Docker](https://circleci.com/docs/2.0/building-docker-images) jobs, both with and without [Docker Layer Caching](https://circleci.com/docs/2.0/docker-layer-caching)
3. Tests writing to and reading from [workspaces](https://circleci.com/docs/2.0/workflows/#using-workspaces-to-share-data-among-jobs)
4. Tests the default `org-global` [context](https://circleci.com/docs/2.0/contexts) (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in the `org-global` context), along with one additional context (likewise needs a key called `MULTI_CONTEXT_END_TO_END_VAR` to exist in an `individual-local` context)
5. Tests upload/storage of [artifacts](https://circleci.com/docs/2.0/artifacts) and [test results](https://circleci.com/docs/2.0/collect-test-data)

To run realitycheck, fork the repository and start building it on your installation of CircleCI.

If you have more ideas for things that should tested, please submit a PR against the open-source repository on GitHub where this project is maintained: <https://github.com/circleci/realitycheck>

See the current CI status of the main repo at <https://circleci.com/gh/circleci/workflows/realitycheck>.

View the LICENSE file in this repository for licensing information.
