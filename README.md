# install-winget
Action to install latest [winget-cli](https://github.com/microsoft/winget-cli) on Windows runners

## Example

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
