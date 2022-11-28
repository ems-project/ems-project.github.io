# Pull Requests

EMS-project uses the [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) strategy to incorporate code changes.

Branches, commits, and GitHub issues MUST respect conventions as described in this document.

UNLESS specified otherwise in the [Branch types](#branch-types) definition, each pull request:

* MUST target the `develop` branch
* MUST use the PR/Commit/Issue Template
* MUST pass installed Travis checks
* MUST be approved by AT LEAST 1 reviewer

## Templates

### Pull Request Template

The template [pull_request_template.md](https://github.com/ems-project/elasticms/blob/4.x/.github/pull_request_template.md) MUST be installed on EMS-project bundles. The template MUST be used when filing a pull request.

### Commit Template

We are using [Conventional commit](https://www.conventionalcommits.org/en/v1.0.0/) as our commit strategy, to simplify generation of release notes.
The template [commit_template.txt](https://github.com/ems-project/elasticms/blob/4.x/.github/git_commit_template.txt) MUST be used for AT LEAST one of the commits in your branch.

To install the template locally run:
`git config --global commit.template <path>/.git_commit_template.txt`

### Issue Template


## Branches

### Branch naming convention

A branch MUST be named `<type>/<short-description>` where:
* `<type>` is one of
   * `feat`
   * `bug`
   * `hot`
   * `maintain`
   * `ref`
* `<short-description>` is a short description separated by `-` dashes explaining the reason of existance of the branch

### Branch types

#### Feature Branch

A `feat/new-feature-description` branch is used to add new functionality to the project. And MUST be approved by AT LEAST 2 reviewers.

* Origin: `develop`
* Merge into: `develop`

#### Bugfix Branch

A `bug/description-of-the-fix` branch is used to patch existing features that are broken.

* Origin: `develop`
* Merge into: `develop`

A bugfix branch MAY contain a new feature if it's tightly coupled to the bugfix itself.

#### Hotfix Branch

A `hot/description-of-the-fix` branch is used to patch a broken feature currently in production.

* Origin: `master`
* Merge into: `master` & `develop`

A hotfix branch MUST be the smallest possible implementation to fix the issue in production.

The pull request MUST target the `master` branch.

#### Maintain Branch

A `maintain/description-of-configuration-change` branch is used to change configurations not related to the project in production. For example: Travis, Phpunit, ...

* Origin: `develop`
* Merge into: `develop`

A maintain branch MUST be used to implement requirements defined by this maintainer repository.

#### Refactoring Branch

A `ref/description-of-refactoring` branch is used to clean dependencies and deprecations in the project. And for refactoring existing code in general.

* Origin: `develop`
* Merge into: `develop`

