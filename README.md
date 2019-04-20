Typedoc nested parameters not rendered bug (union type problem)

See TypeStrong/typedoc#1020

The bug seems to occur only when `tsconfig.json#strict` option is `true`.

At least in this case. The bug report there however report another
repro case for which `strict` is not set (so should be `false`).

Steps:

```
$ yarn install
$ yarn run typedoc --module commonjs --out docs
$ grep "NestedParameter" ./docs/modules/_index_.html
$ echo $?
1
```

Change `strict: false` in `tsconfig.json` then:

```
$ yarn run typedoc --module commonjs --out docs
$ grep "NestedParameter" ./docs/modules/_index_.html
$ echo $?
0
```
