# realitycheck

A sample app that reality-checks some basic CircleCI features in three parallel workflows.

## Running Reality Check on your CircleCI Installation
To run realitycheck, fork/clone the repository and start building it on your installation of CircleCI. Descriptions of the three workflows follow.

### CircleCI Installations using GitHub.com
If you're CircleCI instance is connected with GitHub.com you can fork this repository, and import it to CircleCI from your organization's "Add Project" page.


### CircleCI Installations using GitHub Enterprise
If you're CircleCI instance is connected to a private GitHub Enterprise instance, **you will need to first create an empty repository in GHE** (do not intialize with a README!), and then pull/push this repo to your GHE instance before you can import it to CircleCI from your organization's "Add Project" page.

```
git pull git@github.com:circleci/realitycheck.git && cd realitycheck
git remote set-url origin <your-ghe-repo-url>
git push
```

## Reality Check Workflows

### `resource_class` workflow

Tests all known `resource_class` options—queries the CircleCI API to verify that jobs ran with the requested resources.

- Your instances must be large enough to accomodate these options—see our [Configuration Reference](https://circleci.com/docs/2.0/configuration-reference/#resource_class) for details
- The base URL of your CircleCI installation (e.g., https://circleci.com) must be specified via a `CIRCLE_HOSTNAME` project environment variable
- A personal API token (see `CIRCLE_HOSTNAME/account/api` URL endpoint) must be stored as a `CIRCLE_TOKEN` project environment variable


### VM service workflow

Tests the functionality  of the [`machine` executor](https://circleci.com/docs/2.0/executor-types/#using-machine), [Remote Docker Environment](https://circleci.com/docs/2.0/building-docker-images), and [Docker Layer Caching](https://circleci.com/docs/2.0/docker-layer-caching).


### Features workflow

- Tests ability to save and restore [caches](circleci.com/docs/2.0/caching)
- Tests writing to and reading from [workspaces](https://circleci.com/docs/2.0/workflows/#using-workspaces-to-share-data-among-jobs)
- Tests the default `org-global` [context](https://circleci.com/docs/2.0/contexts) (*NOTE:* needs a key called `CONTEXT_END_TO_END_TEST_VAR` to exist in the `org-global` context)
- Tests multiple contexts (*NOTE:* needs a key called `MULTI_CONTEXT_END_TO_END_VAR` to exist in an `individual-local` context)
- Tests upload/storage of [artifacts](https://circleci.com/docs/2.0/artifacts) and [test results](https://circleci.com/docs/2.0/collect-test-data)


## Contributing

If you have more ideas for things that should tested, please submit a PR against the open-source repository on GitHub where this project is maintained: <https://github.com/circleci/realitycheck>.

See the current CI status of the main repo at <https://circleci.com/gh/circleci/workflows/realitycheck>.

View the LICENSE file in this repository for licensing information.
