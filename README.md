# check-has-semver-label-workflow

This workflow checks that a pull request has exactly one semantic versioning label assigned. Those labels
are:
- no version
- patch
- minor
- major

If the PR doesn't have exactly one of those, the action fails and a status report is posted as a PR comment.

## Usage

### Use pull request from event payload
```yaml
name: Check Has Semver Label

on:
  pull_request:
    - opened
    - synchronize
    - reopened
    - labeled
    - unlabeled

jobs:
  check-has-semver-label:
    permissions:
      pull-requests: write
    uses: infrastructure-blocks/check-has-semver-label-workflow/.github/workflows/check-has-semver-label.yml@v1
```
### Explicitly pass pull request
```yaml
name: Check Has Semver Label

on:
  push: ~

jobs:
  get-current-pr:
    runs-on: ubuntu-22.04
    outputs:
      pr: ${{ steps.get-current-pr.outputs.pr }}
    steps:
      - id: get-current-pr
        uses: 8BitJonny/gh-get-current-pr@2.2.0
  check-has-semver-label:
    needs:
      - get-current-pr
    permissions:
      pull-requests: write
    uses: infrastructure-blocks/check-has-semver-label-workflow/.github/workflows/check-has-semver-label.yml@v1
    with:
      pull-request: ${{ needs.get-current-pr.outputs.pr }}
```

### Releasing

The releasing is handled at git level with semantic versioning tags. Those are automatically generated and managed
by the [git-tag-semver-from-label-workflow](https://github.com/infrastructure-blocks/git-tag-semver-from-label-workflow).
