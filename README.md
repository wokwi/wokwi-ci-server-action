# wokwi-ci-server-action

GitHub Action for running the Wokwi CI server in your GitHub workflow.

## Usage

Add the following step to your workflow:

```yaml
- name: Run a Wokwi CI server
  uses: wokwi/wokwi-ci-server-action@v1
```

You'll usually want to use the [wokwi-ci-action](https://github.com/wokwi/wokwi-ci-action/) right after this action to run your tests on the CI server.
