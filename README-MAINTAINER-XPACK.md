[![license](https://img.shields.io/github/license/xpack-3rd-party/doxygen-awesome-css-xpack)](https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/blob/xpack/LICENSE)
[![CI on Push](https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/actions/workflows/ci.yml/badge.svg)](https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/actions/workflows/ci.yml)
[![GitHub issues](https://img.shields.io/github/issues/xpack-3rd-party/doxygen-awesome-css-xpack.svg)](https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/issues/)
[![GitHub pulls](https://img.shields.io/github/issues-pr/xpack-3rd-party/doxygen-awesome-css-xpack.svg)](https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/pulls)

# Maintainer info

## Project repository

The project is hosted on GitHub:

- <https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack.git>

To clone the stable branch (`xpack`), run the following commands in a
terminal (on Windows use the _Git Bash_ console):

```sh
rm -rf ~/Work/xpack-3rd-party/doxygen-awesome-css-xpack.git && \
mkdir -p ~/Work/xpack-3rd-party && \
git clone \
  https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack.git \
  ~/Work/xpack-3rd-party/doxygen-awesome-css-xpack.git
```

For development purposes, clone the development branch (`xpack-development`):

```sh
rm -rf ~/Work/xpack-3rd-party/doxygen-awesome-css-xpack.git && \
mkdir -p ~/Work/xpack-3rd-party && \
git clone \
  --branch xpack-development \
  https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack.git \
  ~/Work/xpack-3rd-party/doxygen-awesome-css-xpack.git
```

## Prerequisites

A recent [xpm](https://xpack.github.io/xpm/), which is a portable
[Node.js](https://nodejs.org/) command line application.

## How to make new releases

### Release schedule

There are no fixed releases, the project aims to follow the upstream releases.

### Check Git

In the `xpack-3rd-party/doxygen-awesome-css-xpack` Git repo:

- switch to the `xpack-development` branch
- if needed, merge the `xpack` branch

No need to add a tag here, it'll be added when the release is created.

### Increase the version

Determine the upstream version (like `2.3.4`)

- <https://github.com/jothepro/doxygen-awesome-css/releases>

### Merge upstream

- switch to the `main` branch
- merge tag `v2.3.4` from `upstream` into `main`
- push `main` to `origin`

### Update `package.json`

Update the`package.json` file; add an extra digit in the
pre-release field, and initially also add `-pre`,
for example `2.3.4-1-pre`.

### Fix possible open issues

Check GitHub issues and pull requests:

- <https://github.com/xpack-3rd-party/doxygen-awesome-css-xpack/issues/>

and fix them; assign them to a milestone (like `2.3.4-1`).

### Update `README-MAINTAINER-XPACK.md`

Update the `README-MAINTAINER-XPACK.md` file to reflect the changes
related to the new version.

### Update `CHANGELOG-XPACK.md`

- open the `CHANGELOG-XPACK.md` file
- check if all previous fixed issues are in
- add a new entry like _* v2.3.4-1_
- commit with a message like _prepare v2.3.4-1_

### Push changes

- commit and push

### Publish on the npmjs.com server

- select the `xpack-development` branch
- commit all changes
- `npm pack` and check the content of the archive, which should list
  only `package.json`, `README.md`, `LICENSE`, `CHANGELOG-XPACK.md`,
  the `doxygen-awesome-*.js` and `doxygen-custom/*` files;
  possibly adjust `.npmignore`
- `npm version 2.3.4-1`
- push the `xpack-development` branch to GitHub
- the `postversion` npm script should also update tags via `git push origin --tags`

### Publish

- `npm publish --tag next` (use `npm publish --access public` when
  publishing for the first time)

The version is visible at:

- <https://www.npmjs.com/package/@xpack-3rd-party/doxygen-awesome-css?activeTab=versions>

### Update the repo

When the package is considered stable:

- with a Git client (VS Code is fine)
- merge `xpack-development` into `xpack`
- push to GitHub
- select `xpack-development`

### Tag the npm package as `latest`

When the release is considered stable, promote it as `latest`:

- `npm dist-tag ls @xpack-3rd-party/doxygen-awesome-css`
- `npm dist-tag add @xpack-3rd-party/doxygen-awesome-css@2.3.4-1 latest`
- `npm dist-tag ls @xpack-3rd-party/doxygen-awesome-css`
