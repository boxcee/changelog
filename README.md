# @boxcee/changelog

[**semantic-release**](https://github.com/semantic-release/semantic-release) plugin to create or update a changelog file.

> [!WARNING]
> Please consider whether committing release notes to a file is worth the [added complexity](https://semantic-release.gitbook.io/semantic-release/support/faq#should-release-notes-be-committed-to-a-changelog.md-in-my-repository-during-a-release) compared to other available options for capturing release notes.

[![Build Status](https://github.com/boxcee/changelog/workflows/Test/badge.svg)](https://github.com/boxcee/changelog/actions?query=workflow%3ATest+branch%3Amaster) [![npm latest version](https://img.shields.io/npm/v/@boxcee/changelog/latest.svg)](https://www.npmjs.com/package/@boxcee/changelog)
[![npm next version](https://img.shields.io/npm/v/@boxcee/changelog/next.svg)](https://www.npmjs.com/package/@boxcee/changelog)

| Step               | Description                                                                                                                                                                                           |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `verifyConditions` | Verify the `changelogFile` and `changelogTitle` options configuration.                                                                                                                                |
| `prepare`          | Create or update a changelog file in the local project directory with the changelog content created in the [generate notes step](https://github.com/semantic-release/semantic-release#release-steps). |

## Install

```bash
$ npm install @boxcee/changelog -D
```

## Usage

The plugin can be configured in the [**semantic-release** configuration file](https://github.com/semantic-release/semantic-release/blob/master/docs/usage/configuration.md#configuration):

```json
{
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    [
      "@boxcee/changelog",
      {
        "changelogFile": "docs/CHANGELOG.md"
      }
    ],
    [
      "@semantic-release/git",
      {
        "assets": ["docs/CHANGELOG.md"]
      }
    ]
  ]
}
```

With this example, for each release, a `docs/CHANGELOG.md` will be created or updated.

## Configuration

### Options

| Options          | Description                                           | Default        |
| ---------------- | ----------------------------------------------------- | -------------- |
| `changelogFile`  | File path of the changelog.                           | `CHANGELOG.md` |
| `changelogTitle` | Title of the changelog file (first line of the file). | -              |

### Examples

When used with the [@semantic-release/git](https://github.com/semantic-release/git) or [@semantic-release/npm](https://github.com/semantic-release/npm) plugins the `@boxcee/changelog` plugin must be called before those plugins in order to update the changelog file so the [@semantic-release/git](https://github.com/semantic-release/git) and [@semantic-release/npm](https://github.com/semantic-release/npm) plugins can include it in the release.

```json
{
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    "@boxcee/changelog",
    "@semantic-release/npm",
    "@semantic-release/git"
  ]
}
```
