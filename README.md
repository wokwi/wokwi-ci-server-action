# wokwi-ci-server-action

GitHub Action for running the Wokwi CI server in your GitHub workflow.

## Basic usage

Add the following step to your workflow:

```yaml
- name: Run a Wokwi CI server
  uses: wokwi/wokwi-ci-server-action@v1
```

You'll usually want to use the [wokwi-ci-action](https://github.com/wokwi/wokwi-ci-action/) right after this action to run your tests on the CI server.

## Usage as a service container

In some cases, you might want to run the Wokwi CI server as a [service container](https://docs.github.com/en/actions/use-cases-and-examples/using-containerized-services/about-service-containers) in your workflow. This is useful when you want to use an existing container image as the base image for your CI server.

To do this, you can use the `services` option of the workflow's job. Here's an example workflow that uses the [espressif/idf](https://github.com/espressif/idf) container image as the base image for the CI server.

```yaml
jobs:
  container-job:
    container: espressif/idf:latest
    services:
      wokwi-ci-server:
        image: wokwi/wokwi-ci-server
        ports:
          - 3000:3000
    env:
      WOKWI_CLI_SERVER: ws://wokwi-ci-server:3000
```

In this example, the `wokwi-ci-server` service container is started and exposed on port 3000. The `WOKWI_CLI_SERVER` environment variable is set to the URL of the Wokwi CI server.

The wokwi-ci-action will use the `WOKWI_CLI_SERVER` environment variable to determine the URL of the Wokwi CI server.
