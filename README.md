# jq

[![github release](https://img.shields.io/github/v/release/flex-development/jq-action.svg?include_prereleases\&sort=semver)](https://github.com/flex-development/jq-action/releases/latest)
[![test](https://github.com/flex-development/jq-action/actions/workflows/test.yml/badge.svg)](https://github.com/flex-development/jq-action/actions/workflows/test.yml)
[![module type: esm](https://img.shields.io/badge/module%20type-esm-brightgreen)](https://github.com/voxpelli/badges-cjs-esm)
[![license](https://img.shields.io/github/license/flex-development/jq-action.svg)](LICENSE.md)
[![conventional commits](https://img.shields.io/badge/-conventional%20commits-fe5196?logo=conventional-commits\&logoColor=ffffff)](https://conventionalcommits.org)
[![yarn](https://img.shields.io/badge/-yarn-2c8ebb?style=flat\&logo=yarn\&logoColor=ffffff)](https://yarnpkg.com)

Execute JSON queries in GitHub Actions

## Contents

- [What is this?](#what-is-this)
- [Use](#use)
- [Inputs](#inputs)
  - [`data`](#data)
  - [`filter`](#filter)
  - [`options`](#options)
- [Outputs](#outputs)
  - [`result`](#result)
- [Contribute](#contribute)

## What is this?

**TODO**: what is this?

## Use

**TODO**: use

## Inputs

### `data`

The data to operate on.

### `filter`

The filter to apply.

The simplest filter is `.`, which copies `jq`'s input to its output unmodified (except for formatting).
For more advanced filters, see <https://jqlang.github.io/jq/manual>.

### `options`

The command options to apply.

The raw output option, `-r`, will be prepended. With this option, if the [`filter`](#filter)'s result is a string then
it will be written directly to standard output, rather than being formatted as a JSON string with escapes and quotes.

## Outputs

### `result`

The result of the operation.

## Contribute

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

This project has a [code of conduct](./CODE_OF_CONDUCT.md). By interacting with this repository, organization, or
community you agree to abide by its terms.
