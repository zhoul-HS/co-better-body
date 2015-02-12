
# co-better-body

  Parse request bodies with generators inspired by [Raynos/body](https://github.com/Raynos/body).

# Better? WAT?

  [co-body](https://github.com/tj/co-body) has outdated dependencies. plus you can't pass options to qs meaning you're stuck with maximum depth of 5 for parsing forms using object and array notations in field names. Since it seems all but abandoned, and there's quite a few body parsing packages that depend on it, I made some quick changes only updating the `qs` and `raw-body` versions and added passing options to `qs`.

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

// qs depth
var body = yield parse.json(req,  {
    limit: '10kb',
    qs: {
     depth: 10
    }
});

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