<div align="center">
   <img src="https://res.cloudinary.com/adonisjs/image/upload/q_100/v1564392111/adonis-banner_o9lunk.png" width="600px">
</div>

# Password hashing
> Module to hash values with support for [PHC string format](https://github.com/P-H-C/phc-string-format/blob/master/phc-sf-spec.md)

[![circleci-image]][circleci-url] [![npm-image]][npm-url] ![][typescript-image] [![license-image]][license-url]

This module is used by [AdonisJs](https://adonisjs.com) to hash the user password with first class support for upgrading logic. A big thanks to the author of [uphash](https://github.com/simonepri/upash), who inspired me to use [PHC string format](https://github.com/P-H-C/phc-string-format/blob/master/phc-sf-spec.md). I would have used uphash directly, but the user facing API is different from what I desire.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of contents

- [Features](#features)
- [Usage](#usage)
- [Using with AdonisJs](#using-with-adonisjs)
- [Switching drivers](#switching-drivers)
- [Audit report](#audit-report)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Features
1. Support for multiple hashing algorithms.
2. Option to extend and add your own hashing algorithms.
3. Wraps the hash output to a [PHC string format](https://github.com/P-H-C/phc-string-format/blob/master/phc-sf-spec.md), this allows upgrading user passwords, when the underlying configuration changes.

## Usage

Install the package from npm registry as follows:

```sh
npm i @adonisjs/hash

# yarn
yarn add @adonisjs/hash
```

and then use it as follows:

```ts
import { Hash } from '@adonisjs/hash/build/standalone'
const hash = new Hash({}, config)

const hashedValue = await hash.hash('password')
await hash.verify(hashedValue)

await hash.needsRehash(hashedValue) // false
```

## Using with AdonisJs
**The `@adonisjs/core` module includes this module by default**. However, here's how you can set it up manually.

```ts
const providers = [
  '@adonisjs/hash'
]
```

And then also register the typings file inside `tsconfig.json` file.

```json
{
  "files": ["./node_modules/@adonisjs/hash/build/adonis-typings/hash.d.ts"]
}
```

And use it as follows:

```ts
import Hash from '@ioc:Adonis/Core/Hash'
await Hash.hash('password')
```


## Switching drivers
You can switch drivers using the `use` method.

```ts
await Hash.use('bcrypt').hash('password')
```

## Audit report
[Click here](https://htmlpreview.github.io/?https://github.com/adonisjs/hash/blob/develop/npm-audit.html) to see the latest npm audit report.

[circleci-image]: https://img.shields.io/circleci/project/github/adonisjs/hash/master.svg?style=for-the-badge&logo=circleci
[circleci-url]: https://circleci.com/gh/adonisjs/hash "circleci"

[typescript-image]: https://img.shields.io/badge/Typescript-294E80.svg?style=for-the-badge&logo=typescript
[typescript-url]:  "typescript"

[npm-image]: https://img.shields.io/npm/v/@adonisjs/hash.svg?style=for-the-badge&logo=npm
[npm-url]: https://npmjs.org/package/@adonisjs/hash "npm"

[license-image]: https://img.shields.io/npm/l/@adonisjs/hash?color=blueviolet&style=for-the-badge
[license-url]: LICENSE.md "license"
