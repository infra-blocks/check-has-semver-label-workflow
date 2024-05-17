# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.2] - 2024-05-02

### Fixed

- Use `inputs.skip` at step level, and not at job level. Skipping at job level results in the same issue with
  required checks paths as skipping at the caller's workflow invocation site (with an `if` expression).

## [2.2.1] - 2024-04-20

### Fixed

- Usage version of `check-has-semver-label`  to `check-has-semver-label@v2` in README.

## [2.2.0] - 2024-04-20

### Added

- The `skip` input to skip on the callee's side of a `worfklow_call`. Otherwise, when the workflow is skipped from
  the caller's side (with an `if` expression), the check path when the workflow was run is not the same as when
  it was skipped ( `outer / inner` vs. `outer` when skipped) !

## [2.1.0] - 2024-04-18

### Added

- The workflow now gets the current pull request using `get-current-pull-request-action@v1`. This extends the behavior
slightly in that it can now be called from `push` events.

## [2.0.0] - 2024-01-19

### Removed

- The legacy file exporting the workflow. Now the workflow is only accessible at `.github/workflows/workflow.yml`.

## [1.2.0] - 2024-01-19

### Added

- A duplicate of the reusable workflow at the `.github/workflows/workflow.yml`. This is part of a change to have
  every reusable workflow exported under the same conventional path.

## [1.1.4] - 2024-01-17

### Changed

- Clear status report at the beginning of the run.

## [1.1.3] - 2024-01-11

### Changed

- Use `check-labels-action@v2` internally.

## [1.1.2] - 2024-01-11

### Fixed

- Removed concurrency controls that were interfering with caller's workflow.

## [1.1.1] - 2024-01-05

### Fixed

- The `pull-request` input description. GitHub Actions didn't like that it was referencing a context.

## [1.1.0] - 2024-01-05

### Added

- Optional `pull-request` input if the pull request from the event payload is not good enough.

## [1.0.0] - 2024-01-04

### Added

- First release!

[2.2.2]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v2.2.1...v2.2.2
[2.2.1]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v2.2.0...v2.2.1
[2.2.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v2.1.0...v2.2.0
[2.1.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.2.0...v2.0.0
[1.2.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.1.4...v1.2.0
[1.1.4]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.1.3...v1.1.4
[1.1.3]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.1.2...v1.1.3
[1.1.2]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.1.1...v1.1.2
[1.1.1]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/infra-blocks/check-has-semver-label-workflow/releases/tag/v1.0.0
