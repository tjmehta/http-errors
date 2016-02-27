# http-errors

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Node.js Version][node-version-image]][node-version-url]
[![Build Status][travis-image]][travis-url]
[![Test Coverage][coveralls-image]][coveralls-url]

Create HTTP errors for Express, Koa, Connect, etc. with ease.

## Example

```js
var createError = require('http-errors');

app.use(function (req, res, next) {
  if (!req.user) return next(createError(401, 'Please login to view this page.'));
  next();
})
```

## API

This is the current API, currently extracted from Koa and subject to change.

All errors inherit from JavaScript `Error` and the exported `createError.HttpError`.

### Error Properties

- `expose` - can be used to signal if `message` should be sent to the client, defaulting to `false` when `status` >= 500
- `message`
- `status` and `statusCode` - the status code of the error, defaulting to `500`

### createError([status], [message], [properties])

```js
var err = createError(404, 'This video does not exist!');
```

- `status: 500` - the status code as a number
- `message` - the message of the error, defaulting to node's text for that status code.
- `properties` - custom properties to attach to the object

### new createError\[code || name\](\[msg]\))

```js
var err
err = new createError.Continue();                      // 100
err = new createError.SwitchingProtocols();            // 101
err = new createError.Processing();                    // 102
err = new createError.OK();                            // 200
err = new createError.Created();                       // 201
err = new createError.Accepted();                      // 202
err = new createError.NonAuthoritativeInformation();   // 203
err = new createError.NoContent();                     // 204
err = new createError.ResetContent();                  // 205
err = new createError.PartialContent();                // 206
err = new createError.MultiStatus();                   // 207
err = new createError.AlreadyReported();               // 208
err = new createError.IMUsed();                        // 226
err = new createError.MultipleChoices();               // 300
err = new createError.MovedPermanently();              // 301
err = new createError.Found();                         // 302
err = new createError.SeeOther();                      // 303
err = new createError.NotModified();                   // 304
err = new createError.UseProxy();                      // 305
err = new createError.Unused();                        // 306
err = new createError.TemporaryRedirect();             // 307
err = new createError.PermanentRedirect();             // 308
err = new createError.BadRequest();                    // 400
err = new createError.Unauthorized();                  // 401
err = new createError.PaymentRequired();               // 402
err = new createError.Forbidden();                     // 403
err = new createError.NotFound();                      // 404
err = new createError.MethodNotAllowed();              // 405
err = new createError.NotAcceptable();                 // 406
err = new createError.ProxyAuthenticationRequired();   // 407
err = new createError.RequestTimeout();                // 408
err = new createError.Conflict();                      // 409
err = new createError.Gone();                          // 410
err = new createError.LengthRequired();                // 411
err = new createError.PreconditionFailed();            // 412
err = new createError.PayloadTooLarge();               // 413
err = new createError.URITooLong();                    // 414
err = new createError.UnsupportedMediaType();          // 415
err = new createError.RangeNotSatisfiable();           // 416
err = new createError.ExpectationFailed();             // 417
err = new createError.ImATeapot();                     // 418
err = new createError.UnprocessableEntity();           // 422
err = new createError.Locked();                        // 423
err = new createError.FailedDependency();              // 424
err = new createError.UnorderedCollection();           // 425
err = new createError.UpgradeRequired();               // 426
err = new createError.PreconditionRequired();          // 428
err = new createError.TooManyRequests();               // 429
err = new createError.RequestHeaderFieldsTooLarge();   // 431
err = new createError.UnavailableForLegalReasons();    // 451
err = new createError.InternalServerError();           // 500
err = new createError.NotImplemented();                // 501
err = new createError.BadGateway();                    // 502
err = new createError.ServiceUnavailable();            // 503
err = new createError.GatewayTimeout();                // 504
err = new createError.HTTPVersionNotSupported();       // 505
err = new createError.VariantAlsoNegotiates();         // 506
err = new createError.InsufficientStorage();           // 507
err = new createError.LoopDetected();                  // 508
err = new createError.BandwidthLimitExceeded();        // 509
err = new createError.NotExtended();                   // 510
err = new createError.NetworkAuthenticationRequired(); // 511
```

- `code` - the status code as a number
- `name` - the name of the error as a "bumpy case", i.e. `NotFound` or `InternalServerError`.

## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/http-errors.svg?style=flat
[npm-url]: https://npmjs.org/package/http-errors
[node-version-image]: https://img.shields.io/node/v/http-errors.svg?style=flat
[node-version-url]: https://nodejs.org/en/download/
[travis-image]: https://img.shields.io/travis/jshttp/http-errors.svg?style=flat
[travis-url]: https://travis-ci.org/jshttp/http-errors
[coveralls-image]: https://img.shields.io/coveralls/jshttp/http-errors.svg?style=flat
[coveralls-url]: https://coveralls.io/r/jshttp/http-errors
[downloads-image]: https://img.shields.io/npm/dm/http-errors.svg?style=flat
[downloads-url]: https://npmjs.org/package/http-errors
