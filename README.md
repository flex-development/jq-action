# jq

[![github release](https://img.shields.io/github/v/release/flex-development/jq-action.svg?include_prereleases\&sort=semver)](https://github.com/flex-development/jq-action/releases/latest)
[![test](https://github.com/flex-development/jq-action/actions/workflows/test.yml/badge.svg)](https://github.com/flex-development/jq-action/actions/workflows/test.yml)
[![module type: esm](https://img.shields.io/badge/module%20type-esm-brightgreen)](https://github.com/voxpelli/badges-cjs-esm)
[![license](https://img.shields.io/github/license/flex-development/jq-action.svg)](LICENSE.md)
[![conventional commits](https://img.shields.io/badge/-conventional%20commits-fe5196?logo=conventional-commits\&logoColor=ffffff)](https://conventionalcommits.org)
[![yarn](https://img.shields.io/badge/-yarn-2c8ebb?style=flat\&logo=yarn\&logoColor=ffffff)](https://yarnpkg.com)

A [`jq`][jq] utility for GitHub Actions

## Contents

- [What is this?](#what-is-this)
- [Use](#use)
- [Inputs](#inputs)
  - [`data`](#data)
  - [`filter`](#filter)
  - [`options`](#options)
  - [`raw`](#raw)
- [Outputs](#outputs)
  - [`result`](#result)
- [Related](#related)
- [Contribute](#contribute)

## What is this?

This is a simple, but useful, action for executing JSON queries with [`jq`][jq].

## Use

```yaml
---
name: format
on:
  - pull_request
  - push
jobs:
  preflight:
    runs-on: ubuntu-latest
    steps:
      - id: checkout
        name: Checkout ${{ github.head_ref || github.ref_name }}
        uses: actions/checkout@v5.0.0
        with:
          persist-credentials: false
          ref: ${{ github.head_ref || github.ref }}
      - id: version
        name: Get dprint version
        uses: flex-development/jq-action@1.0.0
        with:
          data: package.json
          filter: .devDependencies.dprint
      - id: check
        name: Check formatting
        uses: dprint/check@v2.3
        with:
          args: --config-discovery=false --incremental=false --log-level=info
          config-path: .dprint.jsonc
          dprint-version: ${{ steps.version.outputs.result }}
```

> See [`.github/workflows/test.yml`](.github/workflows/test.yml) for more usage examples.

## Inputs

### `data`

The data to operate on.

### `filter`

The filter to apply.

The simplest filter is `.`, which copies `jq`'s input to its output unmodified (except for formatting).
For more advanced filters, see <https://jqlang.github.io/jq/manual>.

### `options`

The command options to apply (optional).

### `raw`

> **default**: `true`

Shortcut for the raw output option, `-r`.

With this option, if the [`result`](#result) of the [`filter`](#filter) is a string, it will not be formatted as a JSON
string with escapes and quotes.

## Outputs

### `result`

The result of the [`filter`](#filter).

## Related

- [`flex-development/manver-action`][manver-action] — version metadata extraction utility

## Contribute

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

This project has a [code of conduct](./CODE_OF_CONDUCT.md). By interacting with this repository, organization, or
community you agree to abide by its terms.

[jq]: https://jqlang.github.io/jq

[manver-action]: https://github.com/flex-development/manver-action
