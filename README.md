# install-winget

Action to install [winget-cli](https://github.com/microsoft/winget-cli) default v1.8.1911 on Windows runners. Other versions can be installed by changing `wget_release_id` parameter.

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
      with:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        wget_release_id: latest

    - name: Install wingetcreate
      run: winget install wingetcreate --disable-interactivity --accept-source-agreements
```

### Inputs

#### `GITHUB_TOKEN` (Optional)

The GitHub token to use when interacting with the GitHub API. Used to bypass unauthenticated rate limits.

**Recommendation is to set this to ${{ secrets.GITHUB_TOKEN }} or some other available token** as GitHub runners tend to often come with exhausted rate limits.

#### `wget_release_id` (Optional)

This is used to be able to pin (make immutable) the version of winget that is taken github. To see which versions (you need the release-id) is possible to use plese check the github API for the release of [winget-cli](https://github.com/microsoft/winget-cli) this can be checked by looking for the topmost `id:` attribute here: https://api.github.com/repos/microsoft/winget-cli/releases . 

### Outputs

#### `winget-version`

The output of `winget --version` for the installed version.

```yml
    - uses: Cyberboss/install-winget@v1
      id: stepid

    - run: echo '${{ steps.stepid.outputs.winget-version }}' # i.e. v1.6.1573-preview
```
