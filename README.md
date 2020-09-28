# sidetree.js

[![npm version](https://badge.fury.io/js/sidetree.js.svg)](https://badge.fury.io/js/sidetree.js) ![Continuous Integration](https://github.com/transmute-industries/sidetree.js/workflows/CI/badge.svg)

Sidetree.js is an implementation of the Sidetree protocol, implementation [v0.1.0 of the specification](https://web.archive.org/web/20200721150053/https://identity.foundation/sidetree/spec/v0.1.0/)

This codebase is a [Lerna monorepo](https://github.com/lerna/lerna). Here is a list of the packages it currently contains: https://github.com/transmute-industries/sidetree.js/tree/master/packages

## Usage

To install all packages run

```bash
npm install
```

To run tests in every packages run

```bash
npm run test
```

To run tests in a specific package run

```bash
npm t -- --scope @sidetree/did-method-element
```

## Services

We use docker-compose to setup the services used in tests, Namely:

- ganache: for a local ethereum testnet
- ipfs: for a local ipfs node
- mongodb: for a local mongo DB

Make sure you have `docker` and `docker-compose` installed before running the tests

## How to pull individual packages from the mono repo

- Copy the global eslint config to the package
- Make sure the linked packages are published

## Release process

### Unstable releases

Unstable releases are automatic, from CD:

- On every commit to master an unstable release is pushed. An unstable release is a release with a tag of the form: vA.B.C-unstable.X. Everytime a PR is merged, X is incremented.
- If "skip-ci" is present in the commit message, the aforementioned behavior is skipped

### Stable releases

Stable releases are triggered by a dev locally

- Make sure you are familiar with [Semantic Versioning](https://semver.org/)
- Run `npm install` and `npm build` in the root level directory
- Run
  - `npm run publish:stable:patch` for a patch version increment
  - `npm run publish:stable:minor` for a minor version increment
  - `npm run publish:stable:major` for a major version increment

### Example

- Current version is v0.1.0
- A PR is made to fix bug A. When it's merged a release is made: v0.1.0-unstable-0
- A PR is made to add feature B. When it's merged a release is made: v0.1.0-unstable-1
- A PR is made to add feature C. When it's merged a release is made: v0.1.0-unstable-2
- Dev runs `npm run publish:stable:patch`. Current version is v0.1.0
- A PR is made to fix bug D. When it's merged a release is made: v0.1.1-unstable-0
- etc...

### Docker Commands

You may find it useful to prune all docker data:

```
docker system prune
```

## License

Some portions of this software have been copied from [decentralized-identity/sidetree](https://github.com/decentralized-identity/sidetree).

In some cases no changes were made, in others, substantial changes were made to support modularity, independent versioning, seperation of concerns, and incremental security upgrades.

For more information see [decentralized-identity/sidetree LICENSE](https://github.com/decentralized-identity/sidetree/blob/master/LICENSE).

Unless otherwise noted the following license applies:

```
Copyright 2020 - Transmute Industries Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
