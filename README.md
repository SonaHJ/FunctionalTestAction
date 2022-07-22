## HCL OneTest UI

This action enables you to run HCL OneTest UI tests.

## How this works
You can use the Traditional UI Action that enables you to select any type of test created in HCL OneTest™ UI that you can add to the job in the GitHub action.

## Pre requisites

1. Create a github repository
2. Create a folder named ".github" in the root of the repository
3. Create a folder named "workflows" inside the ".github" folder.
5. Create a .yml file with any name , inside the "workflow" folder and you need to code as following example in that yml file
## Example usage

```yaml
name: HCL OneTest UI

on:
    workflow_dispatch:
        inputs:
            projectdir:
                description: 'Project Directory'
                required: true
            suite:
                description: 'Test Suite Name'
                required: true
            logformat:
                description: 'Log Format'
                required: false
            userargs:
                description: 'User Arguments'
                required: false
            itercount:
                description: 'Iteration Count'
                required: false

jobs:

    UI-Action:
        runs-on: self-hosted
        name: HCL OneTest UI
        steps:
         - name: HCL OneTest UI
           uses: SonaHJ/TraditionalUIAction@HCLOneTestUI_02
           with:
            projectdir: '${{ github.event.inputs.projectdir }}'
            suite: '${{ github.event.inputs.suite }}'
            logformat: '${{ github.event.inputs.logformat }}'
            userargs: '${{ github.event.inputs.userargs }}'
            itercount: '${{ github.event.inputs.itercount }}'

```
7. Replace the example input values with your details.
8. Push it into the main branch
9. Go to the Actions section in the repository and select the workflow.
10. Click the Run workflow dropdown and the list of input boxes get displayed.

To configure agent:
1. Go to settings (Repo).
2. Select action -> runner.
3. Click Create self-hosted runner, follow the download and configure instruction

## Inputs

### `projectdir`

**Required** Fully qualified path to the HCL OneTest UI project directory.

### `suite`

**Required** Name of the script to be executed without the extension. For eg., Script1 or TestFolder.Script1 in case Script1 is in a folder named TestFolder.

### `logformat`

Format of script execution logs. Choose from Default, none, json, xml, html, text, and TPTP.

### `userargs`

Additional playback arguments, if any. If there are multiple arguments, you must enclose each argument within double quotes and separate the arguments by providing a space between them.

### `itercount`
Number of dataset iterations to be run.
