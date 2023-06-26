# InstallWinget
Action to install latest winget CLI on Windows runners

## Usage

```yml
jobs:
  test-job:
    name: Test Job
    runs-on: windows-latest
    steps:
    - name: Install winget
      uses: Cyberboss/InstallWinget@v1
```
