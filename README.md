# Unity - Test runner
[![Actions status](https://github.com/webbertakken/unity-test-runner/workflows/Actions%20%F0%9F%98%8E/badge.svg)](https://github.com/webbertakken/unity-test-runner/actions?query=branch%3Amaster+workflow%3A%22Actions+%F0%9F%98%8E%22)

---

GitHub Action to 
[run tests](https://github.com/marketplace/actions/unity-test-runner) 
for any Unity project. 

Part of the 
[Unity Actions](https://github.com/webbertakken/unity-actions) 
collection.

---

This is a recommended step to prepare your pipeline for using the 
[Build](https://github.com/webbertakken/unity-actions#build)
action. This action also requires the [activation](https://github.com/marketplace/actions/unity-activate) step.

## Documentation

See the 
[Unity Actions](https://github.com/webbertakken/unity-actions)
collection repository for workflow documentation and reference implementation.

## Usage

Create or edit the file called `.github/workflows/main.yml` and add a job to it.

```yaml
name: Test project
on: [push]
jobs:
  testRunnerInAllModes:
    name: Test all modes ✨
    runs-on: ubuntu-latest
    steps:
```

Configure the test runner as follows:

```yaml
      # Configure test runner
      - name: Run tests
        id: myTestStep
        uses: webbertakken/unity-test-runner@v1.1
        env:
          # Choose: "all", "playmode", "editmode"
          TEST_MODE: all
          
          # Optional: Path to your project, leave blank for "./"
          PROJECT_PATH: relative/path/to/your/project

          # Optional: Artifacts path, leave blank for "artifacts"
          ARTIFACTS_PATH: store/artifacts/here
```

You use the id to **upload the artifacts** like so:

```yaml
      # Upload artifacts
      - name: Upload test results
        uses: actions/upload-artifact@v1
        with:
          name: Test results
          path: ${{ steps.myTestStep.outputs.artifactsPath }}
```

Commit and push your workflow definition.

## More actions

Visit 
[Unity Actions](https://github.com/webbertakken/unity-actions) 
to find related actions for Unity.

Feel free to contribute.

## Licence 

[MIT](./LICENSE)
