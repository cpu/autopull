# zlint autopull

[![Build Status](https://travis-ci.com/cpu/zlint-autopull.svg?branch=master)](https://travis-ci.com/cpu/zlint-autopull)

Bash script that auto-creates Pull Requests for
[zlint](https://github.com/zmap/zlint)'s gtld data.

Forked from https://github.com/nbio/autopull and tailored to Go, `zlint` and
Travis CI.

## How it works

1. Clones the to-be-updated repo (`AP_REPO`) into a tmp dir
1. Does stuff (`AP_CMD`)
1. Creates a PR for the changes
1. Profit!

## Configuration

This script uses environment variables for configuration; most must be set.

- `AP_REPO` — GitHub repository to auto-update, in the form of `user/repo`, e.g. `zmap/zlint`
- `AP_BRANCH` — Branch to check out. Default: `master`
- `AP_CMD` — Update command that mutates the repository. Default: `go generate ./...`
- `GH_USER` — GitHub username
- `GH_PASSWORD` — GitHub user password (for cloning the repo)
- `GH_TOKEN` – GitHub [access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) (not your password!)
- `GIT_AUTHOR_NAME` and `GIT_COMMITTER_NAME` — Name of the user or robot doing the committing. Both must be set.
- `GIT_AUTHOR_EMAIL` and `GIT_COMMITTER_EMAIL` — Email address of the user or robot doing the committing. Both must be set.

## Travis quickstart

1. Clone (or fork) this repository
1. Tweak `.travis.yml` if you need to install prereqs for the `AP_CMD`
1. Add the `GH_USER` as a collaborator on your `AP_REPO` to push PR branches
1. Enable Travis CI for the repository
1. Configure all of the required environment variables in the Travis UI (be sure
   not to allow displaying the `GH_TOKEN` or `GH_PASSWORD` env vars in the log)
1. Enable a daily cron build of master

## Credits

Original © 2018 nb.io, LLC
