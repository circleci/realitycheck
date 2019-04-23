# realitycheck

A sample app that validates some basic CircleCI features in three parallel workflows.

To run realitycheck, fork the repository and start building it on your installation of CircleCI. See [Using realitycheck to validate your CircleCI installation](https://support.circleci.com/hc/en-us/articles/360011235534) from the CircleCI Support Center for details on forking the project and building it on your CircleCI installation.

`realitycheck` is split into three [workflows](https://circleci.com/docs/2.0/workflows/) that each consist of a series of [jobs](https://circleci.com/docs/2.0/jobs-steps/) that test [resource class](https://circleci.com/docs/2.0/configuration-reference/#resource_class), [VM service](https://circleci.com/docs/2.0/executor-types/#using-machine) (only available on AWS installs), and features (e.g. caching, artifacts, contexts) functionality. More details below.

You may experience failed builds around [environment variables](https://circleci.com/docs/2.0/env-vars/) and [contexts](https://circleci.com/docs/2.0/contexts/) after running building this project on CircleCI for the first time. In order to properly test functionality, please set the following environment variables and contexts from within the CircleCI using the instructions below.

## Setting Environment Variables and Contexts
### Project Environment Variables
Set environment variables at `http(s)://{$CIRCLECI_URI}/gh/{$USER_NAME}/realitycheck/edit#env-vars`.
  
- The base URL of your CircleCI installation (e.g. https://circleci.com) must be specified via a `CIRCLE_HOSTNAME` project environment variable
- A personal API token (see `CIRCLE_HOSTNAME/account/api` [endpoint](https://circleci.com/docs/api/#add-an-api-token)) must be stored as a `CIRCLE_TOKEN` project environment variable

### Contexts
Set contexts at `http(s)://{$CIRCLECI_URI}/gh/organizations/{$org|username}/settings#contexts`
- Add a key called `MULTI_CONTEXT_END_TO_END_VAR` with any value to exist in a context called `individual-local`
- Add a key called `CONTEXT_END_TO_END_TEST_VAR` with any value to exist in a context called `org-global`

## Workflows 
### `resource_class` workflow
Tests all known `resource_class` options, and queries the CircleCI API to verify that jobs ran with the requested resources.

Your Nomad clients must be large enough to accommodate these options—see our [Configuration Reference](https://circleci.com/docs/2.0/configuration-reference/#resource_class) for more details.

### VM service workflow
Tests the functionality  of the [`machine` executor](https://circleci.com/docs/2.0/executor-types/#using-machine), [Remote Docker Environment](https://circleci.com/docs/2.0/building-docker-images), and [Docker Layer Caching](https://circleci.com/docs/2.0/docker-layer-caching). These features are only supported in an AWS install using [`enterprise-setup`](https://github.com/circleci/enterprise-setup) today.

### Features workflow
- Tests ability to save and restore [caches](circleci.com/docs/2.0/caching).
- Tests writing to and reading from [workspaces](https://circleci.com/docs/2.0/workflows/#using-workspaces-to-share-data-among-jobs).
- Tests the default `org-global` [context](https://circleci.com/docs/2.0/contexts) (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in a context called `org-global`) .
- Tests multiple contexts (*NOTE:* needs a key called `MULTI_CONTEXT_END_TO_END_VAR` to exist in a context called `individual-local`).
- Tests upload/storage of [artifacts](https://circleci.com/docs/2.0/artifacts) and [test results](https://circleci.com/docs/2.0/collect-test-data).


## Contributing
If you have more ideas for things that should tested, please submit a PR against the open-source repository on GitHub where this project is maintained: <https://github.com/circleci/realitycheck>.

See the current CI status of the main repo at <https://circleci.com/gh/circleci/workflows/realitycheck>.

View the LICENSE file in this repository for licensing information.
