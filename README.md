# Witcher API testing tool Github Action

Easy-to-use GitHub Action to use Witcher.

## Usage

Add `witcher-workflow` to the workflow of your application. The below example will run `witcher` with joystick config
and will fail if any of the tests fail.

```yaml
name: API test

on:
  workflow_dispatch:

jobs:
  api-test:
    runs-on: ubuntu-latest
    name: API test
    steps:
      - name: Run Witcher API test
        steps:
          - name: Run Witcher API test
            uses: getjoystick/witcher-action
            with:
              source: joystick
              apiKey: ${{ secrets.API_TEST_JOYSTICK_API_KEY }}
              configId: "root-config-id"
              # Specifying `secretJson` is optional, read `witcher` documentation for more info
              secretJson: ${{ secrets.API_TEST_SECRETS_JSON }}
```

To run `witcher` with local config, use the following example:

```yaml
name: API test

on:
  workflow_dispatch:

jobs:
  api-test:
    runs-on: ubuntu-latest
      name: API test
      steps:
        - name: Checkout
          uses: actions/checkout@v3
        - name: Run Witcher API test
          uses: getjoystick/witcher-action
          with:
            source: local
            localConfigPath: ./test/root-jsonplaceholder.json
            # Specifying `secretJson` is optional, read `witcher` documentation for more info
            secretJson: ${{ secrets.API_TEST_SECRETS_JSON }}
```
