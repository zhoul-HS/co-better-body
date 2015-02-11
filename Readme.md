
# co-body

  Parse request bodies with generators inspired by [Raynos/body](https://github.com/Raynos/body).

## Installation

```
$ npm install co-body
```

## Options

  Available via [raw-body](https://github.com/stream-utils/raw-body/blob/master/index.js):

  - `limit` number or string representing the request size limit (1mb for json and 56kb for form-urlencoded)

  Available via [qs](https://github.com/hapijs/qs):

  - `depth` number representing the parsed object maximum hierarchy depth, default `5`
  - `delimiter` string or regex representing the query string delimeter, default `&`
  - `arrayLimit` nubmer representing the maximum array size or -1 to disable arrays, default `20`

## Example

```js
// application/json
var body = yield parse.json(req);

// explicit limit
var body = yield parse.json(req, { limit: '10kb' });

// application/x-www-form-urlencoded
var body = yield parse.form(req);

// either
var body = yield parse(req);
```

## Koa

  This lib also supports `ctx.req` in Koa (or other libraries),
  so that you may simply use `this` instead of `this.req`.

```js
// application/json
var body = yield parse.json(this);

// application/x-www-form-urlencoded
var body = yield parse.form(this);

// either
var body = yield parse(this);
```

# License

  MIT