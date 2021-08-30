# Release Drafter Example

A project that we use to demonstrate the [release-drafter](https://github.com/marketplace/actions/release-drafter) GitHub Action.

This works in two phases.

## Pull Request Auto Labeler

When a pull request opens, tags are added to the PR based on the branch name/title/description.

As configured in this repo, the following labels are automatically added:

- `feature` if the branch name starts with "feature"
- `patch-fix` if the branch name starts with "fix"
- `chore` if the branch name starts with "chore"
- `breaking-change` if the *pull request title* contains the word "breaking"

## Releaser

When the main branch gets a new commit (including a PR merge) the next draft release is built based on the unreleased commits.

When release notes are being drafted, semantic versioning is followed: `major`.`minor`.`patch`

_For this to give the next draft release a name, you must already have an existing release, since numbering will be continued from there._

The default is that a "minor" release is drafted, which bumps the version `minor`.

But if _all_ PRs in the release are tagged `patch-fix` or `chore`, a patch release is drafted, bumping the version `patch`.

But if _any_ PR in the release is tagged `breaking-change`, a major release is drafted, bumping the version `major`.

## Testing this repository

1. Add something to the bottom of `test.md`.
2. Commit it in a new branch.
3. Open a PR for the new branch.
4. Merge the PR.
5. Verify that the PR was added to the latest unpublished release.
