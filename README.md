# `deno_lint`

A Rust crate for writing fast JavaScript and TypeScript linters.

This crate powers [`deno lint`](https://deno.land/manual/tools/linter), but is not Deno specific 
and can be used to write linters for Node as well.

---

**NOTE**
Work-in-progress

*Current focus is on getting `recommended` set of rules from ESLint and `@typescript-eslint`
working out of the box.*

See [the roadmap](https://github.com/denoland/deno_lint/issues/176)

---

## Performance

Blazing fast, see comparison with ESLint:

```
[
  {
    "name": "deno_lint",
    "totalMs": 830.5838349999995,
    "runsCount": 5,
    "runsAvgMs": 166.1167669999999,
    "runsMs": [
      163.71872200000007,
      160.46893499999987,
      169.2397719999999,
      167.75393099999974,
      169.40247499999987
    ]
  },
  {
    "name": "eslint",
    "totalMs": 11783.570954999997,
    "runsCount": 5,
    "runsAvgMs": 2356.7141909999996,
    "runsMs": [
      2559.053129,
      2383.412156999999,
      2261.1746249999997,
      2306.645263999999,
      2273.28578
    ]
  }
]
```

*Benchmarks are run during CI on Ubuntu, using the same set of rules for both linters.
Test subject is [`oak` server](https://github.com/oakserver/oak) consisting of about 50 files.
See [`./benchmarks/`](./benchmarks/) directory for more info.*

## Supported rules

- [`ban-ts-comment`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/ban-ts-comment.md)
- `ban-ts-ignore`
- [`ban-types`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/ban-types.md)
- `ban-untagged-ignore`
- `ban-untagged-todo`
- [`constructor-super`](https://eslint.org/docs/rules/constructor-super)
- [`default-param-last`](https://eslint.org/docs/rules/default-param-last)
- [`eqeqeq`](https://eslint.org/docs/rules/eqeqeq)
- [`explicit-function-return-type`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/explicit-function-return-type.md)
- [`for-direction`](https://eslint.org/docs/rules/for-direction)
- [`getter-return`](https://eslint.org/docs/rules/getter-return)
- [`no-array-constructor`](https://eslint.org/docs/rules/no-array-constructor)
- [`no-async-promise-executor`](https://eslint.org/docs/rules/no-async-promise-executor)
- [`no-await-in-loop`](https://eslint.org/docs/rules/no-await-in-loop)
- [`no-case-declarations`](https://eslint.org/docs/rules/no-case-declarations)
- [`no-class-assign`](https://eslint.org/docs/rules/no-class-assign)
- [`no-compare-neg-zero`](https://eslint.org/docs/rules/no-compare-neg-zero)
- [`no-cond-assign`](https://eslint.org/docs/rules/no-cond-assign)
- [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign)
- [`no-debugger`](https://eslint.org/docs/rules/no-debugger)
- [`no-delete-var`](https://eslint.org/docs/rules/no-delete-var)
- [`no-dupe-args`](https://eslint.org/docs/rules/no-dupe-args)
- [`no-dupe-class-members`](https://eslint.org/docs/rules/no-dupe-class-members)
- [`no-dupe-else-if`](https://eslint.org/docs/rules/no-dupe-else-if)
- [`no-dupe-keys`](https://eslint.org/docs/rules/no-dupe-keys)
- [`no-duplicate-case`](https://eslint.org/docs/rules/no-duplicate-case)
- [`no-empty-character-class`](https://eslint.org/docs/rules/no-empty-character-class)
- [`no-empty-interface`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-empty-interface.md)
- [`no-empty-pattern`](https://eslint.org/docs/rules/no-empty-pattern)
- [`no-empty`](https://eslint.org/docs/rules/no-empty)
- [`no-eval`](https://eslint.org/docs/rules/no-eval)
- [`no-ex-assign`](https://eslint.org/docs/rules/no-ex-assign)
- [`no-explicit-any`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-explicit-any.md)
- [`no-extra-boolean-cast`](https://eslint.org/docs/rules/no-extra-boolean-cast)
- [`no-extra-non-null-assertion`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-extra-non-null-assertion.md)
- [`no-extra-semi`](https://eslint.org/docs/rules/no-extra-semi)
- [`no-func-assign`](https://eslint.org/docs/rules/no-func-assign)
- [`no-inferrable-types`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-inferrable-types.md)
- [`no-misused-new`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-misused-new.md)
- [`no-namespace`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-namespace.md)
- [`no-new-symbol`](https://eslint.org/docs/rules/no-new-symbol)
- [`no-non-null-assertion`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-non-null-assertion.md)
- [`no-obj-calls`](https://eslint.org/docs/rules/no-obj-calls)
- [`no-octal`](https://eslint.org/docs/rules/no-octal)
- [`no-prototype-builtins`](https://eslint.org/docs/rules/no-prototype-builtins)
- [`no-regex-spaces`](https://eslint.org/docs/rules/no-regex-spaces)
- [`no-setter-return`](https://eslint.org/docs/rules/no-setter-return)
- [`no-shadow-restricted-names`](https://eslint.org/docs/rules/no-shadow-restricted-names)
- `no-sparse-array`
- [`no-this-alias`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/no-this-alias.md)
- [`no-this-before-super`](https://eslint.org/docs/rules/no-this-before-super)
- [`no-throw-literal`](https://eslint.org/docs/rules/no-throw-literal)
- [`no-unsafe-finally`](https://eslint.org/docs/rules/no-unsafe-finally)
- [`no-unsafe-negation`](https://eslint.org/docs/rules/no-unsafe-negation)
- [`no-unused-labels`](https://eslint.org/docs/rules/no-unused-labels)
- [`no-var`](https://eslint.org/docs/rules/no-var)
- [`no-with`](https://eslint.org/docs/rules/no-with)
- [`prefer-as-const`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/prefer-as-const.md)
- [`prefer-namespace-keyword`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/prefer-namespace-keyword.md)
- [`require-yield`](https://eslint.org/docs/rules/require-yield)
- `single-var-declarator`
- [`triple-slash-reference`](https://github.com/typescript-eslint/typescript-eslint/blob/master/packages/eslint-plugin/docs/rules/triple-slash-reference.md)
- [`use-isnan`](https://eslint.org/docs/rules/use-isnan)
- [`valid-typeof`](https://eslint.org/docs/rules/valid-typeof)

## Ignore directives

### Files

To ignore whole file `// deno-lint-ignore-file` directive should placed at the top of the file.

```ts
// deno-lint-ignore-file

function foo(): any {
  // ...
}
```

Ignore directive must be placed before first stament or declaration:

```ts
// Copyright 2020 the Deno authors. All rights reserved. MIT license.

/**
 * Some JS doc
 **/

// deno-lint-ignore-file

import { bar } from "./bar.js";

function foo(): any {
  // ...
}
```

### Diagnostics

To ignore certain diagnostic `// deno-lint-ignore <codes...>` directive should be placed
before offending line.

```ts
// deno-lint-ignore no-explicit-any
function foo(): any {
  // ...
}

// deno-lint-ignore no-explicit-any explicit-function-return-type
function bar(a: any) {
  // ...
}
```

Specyfing rule code that will be ignored is required.

## Example

`examples/dlint/main.rs` provides a minimal standalone binary demonstrating
how `deno_lint` can be used as a crate. 

```shell
$ ▶ target/debug/examples/dlint ../deno/std/http/server.ts ../deno/std/http/file_server.ts
(no-empty) Empty block statement
  --> ../deno/std/http/server.ts:93:14
   |
93 |       } catch {}
   |               ^^
   |
(no-empty) Empty block statement
   --> ../deno/std/http/server.ts:111:44
    |
111 |     while ((await body.read(buf)) !== null) {}
    |                                             ^^
    |
(no-empty) Empty block statement
   --> ../deno/std/http/server.ts:120:41
    |
120 |   constructor(public listener: Listener) {}
    |                                          ^^
    |
(ban-untagged-todo) TODO should be tagged with (@username) or (#issue)
 --> ../deno/std/http/file_server.ts:5:0
  |
5 | // TODO Stream responses instead of reading them into memory.
  | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  |
(ban-untagged-todo) TODO should be tagged with (@username) or (#issue)
 --> ../deno/std/http/file_server.ts:6:0
  |
6 | // TODO Add tests like these:
  | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  |
(ban-untagged-todo) TODO should be tagged with (@username) or (#issue)
   --> ../deno/std/http/file_server.ts:137:0
    |
137 | // TODO: simplify this after deno.stat and deno.readDir are fixed
    | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    |
(no-empty) Empty block statement
   --> ../deno/std/http/file_server.ts:155:16
    |
155 |     } catch (e) {}
    |                 ^^
    |
Found 7 problems
```

For more concrete implementation visit [`deno`](https://github.com/denoland/deno/blob/master/cli/lint.rs)

## Developing

Make sure to have latest stable version of Rust installed (1.44.0).

```shell
// check version
$ rustc --version
rustc 1.44.0 (49cae5576 2020-06-01)

// build all targets
$ cargo build --all-targets

// test it
$ cargo test
```

## Contributing

- If you are going to work on an issue, mention so in the issue comments
  _before_ you start working on the issue.

- Please be professional in the forums. We follow
  [Rust's code of conduct](https://www.rust-lang.org/policies/code-of-conduct)
  (CoC) Have a problem? Email ry@tinyclouds.org.

- Ask for help in the [community chat room](https://discord.gg/TGMHGv6).

## Submitting a Pull Request

Before submitting, please make sure the following is done:

1. That there is a related issue and it is referenced in the PR text.
2. There are tests that cover the changes.
3. Ensure `cargo test` passes.
4. Format your code with `deno run --allow-run tools/format.ts`
5. Make sure `deno run --allow-run tools/lint.ts` passes.
