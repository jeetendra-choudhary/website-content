---
title: Semantic Versioning using npm
description: "Semantic Versioning is a convention used to provide a meaning to versions"
date: 2018-08-05T15:00:00+02:00
tags: node
tags_weight: 9
path: npm-semantic-versioning
---

If there's one great thing in Node.js packages, is that all agreed on using Semantic Versioning for their version numbering.

The Semantic Versioning concept is simple: all versions have 3 digits: `x.y.z`.

- the first digit is the major version
- the second digit is the minor version
- the third digit is the patch version

When you make a new release, you don't just up a number as you please, but you have rules:

- you up the major version when you make incompatible API changes
- you up the minor version when you add functionality in a backward-compatible manner
- you up the patch version when you make backward-compatible bug fixes

The convention is adopted all across programming languages, and it is very important that every `npm` package adheres to it, because the whole system depends on that.

Why is that so important?

Because `npm` set some rules we can use in the [`package.json` file](https://flaviocopes.com/package-json/) to choose which versions it can update our packages to, when we run `npm update`.

The rules use those symbols:

- `^`
- `~`
- `>`
- `>=`
- `<`
- `<=`
- `=`
- `-`
- `||`

Let's see those rules in detail:

- `^`: if you write `^0.13.0` when running `npm update` it can update to patch and minor releases: `0.13.1`, `0.14.0` and so on.
- `~`: if you write `~0.13.0`, when running `npm update` it can update to patch releases: `0.13.1` is ok, but `0.14.0` is not.
- `>`: you accept any version higher than the one you specify
- `>=`: you accept any version equal to or higher than the one you specify
- `<=`: you accept any version equal or lower to the one you specify
- `<`: you accept any version lower to the one you specify
- `=`: you accept that exact version
- `-`: you accept a range of versions. Example: `2.1.0 - 2.6.2`
- `||`: you combine sets. Example: `< 2.1 || > 2.6`

You can combine some of those notations, for example use `1.0.0 || >=1.1.0 <1.2.0` to either use 1.0.0 or one release from 1.1.0 up, but lower than 1.2.0.

There are other rules, too:

- no symbol: you accept only that specific version you specify (`1.2.1`)
- `latest`: you want to use the latest version available