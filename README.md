# install-winget

Action to install latest [winget-cli](https://github.com/microsoft/winget-cli) on Windows runners

Currently only supports `windows-2022`/`window-latest` runner image.

## Usage

```yml
    - name: Install winget
      uses: Cyberboss/install-winget@v1
```

### Example

`.github/workflows/test-job.yml`
```yml
jobs:
  test-job:
    name: Test Job
    runs-on: windows-latest
    steps:
    - name: Install winget
      uses: Cyberboss/install-winget@v1
      
    - name: Install wingetcreate
      run: winget install wingetcreate --disable-interactivity --accept-source-agreements
```

## Outputs

### `winget-version`

The output of `winget --version` for the installed version.

```yml
    - uses: Cyberboss/install-winget@v1
      id: stepid

    - run: echo '${{ steps.stepid.outputs.winget-version }}' # i.e. v1.6.1573-preview
```
