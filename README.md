# fastify-workflows-community

> **Warning**  
> Move to [fastify-userland/workflows](https://github.com/fastify-userland/workflows)

This is the github workflows for the fastify plugin community.

Inspired by: [fastify/workflows](fastify/workflows)

> Reason for creation: `fastify` Mainly used for plugins managed by the fastify organization. less applicable to the community. (For more information on this, please see: [fastify/workflows#36](fastify/workflows#36))

## Usage

A reusable workflow is called by using the uses keyword in another workflow:

```yml
name: CI

on:
  push:
    paths-ignore:
      - 'docs/**'
      - '*.md'
  pull_request:
    paths-ignore:
      - 'docs/**'
      - '*.md'

jobs:
  npm:
    uses: BlackHole1/fastify-workflows-community/.github/workflows/plugin-ci-npm.yml@v1.1
    with:
      lint: true

  yarn:
    uses: BlackHole1/fastify-workflows-community/.github/workflows/plugin-ci-yarn.yml@v1.1

  pnpm:
    uses: BlackHole1/fastify-workflows-community/.github/workflows/plugin-ci-pnpm.yml@v1.1
```

### Inputs

#### npm

| Input Name          | Required | Type    | Default                        | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------ | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                        | Set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                           | Version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `npm run lint`                 | npm run lint script.                                                     |
| `install-script`    | false    | string  | `npm install --ignore-scripts` | npm run install script.                                                  |
| `test-script`       | false    | string  | `npm run test:ci`              | npm run test script.                                                     |
| `coveralls`         | false    | boolean | `false`                        | enable coveralls.                                                        |

#### yarn

| Input Name          | Required | Type    | Default                                           | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------------------------- | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                                           | Set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                                              | Version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `yarn run lint`                                   | Yarn run lint script.                                                    |
| `install-script`    | false    | string  | `yarn install --ignore-scripts --frozen-lockfile` | Yarn run install script.                                                 |
| `test-script`       | false    | string  | `yarn run test:ci`                                | Yarn run test script.                                                    |
| `coveralls`         | false    | boolean | `false`                                           | enable coveralls.                                                        |

#### pnpm

| Input Name          | Required | Type    | Default                         | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------- | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                         | set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                            | version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `pnpm run lint`                 | pnpm run lint script.                                                    |
| `install-script`    | false    | string  | `pnpm install --ignore-scripts` | pnpm run install script.                                                 |
| `test-script`       | false    | string  | `pnpm run test:ci`              | pnpm run test script.                                                    |
| `coveralls`         | false    | string  | `false`                         | enable coveralls.                                                        |
| `pnpm-version`      | false    | boolean | `7.4.0`                         | install pnpm version.                                                    |

[fastify/workflows]: https://github.com/fastify/workflows
[fastify/workflows#36]: https://github.com/fastify/workflows/pull/36
