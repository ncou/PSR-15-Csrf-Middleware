# PSR-15 Middleware
[![Build Status](https://travis-ci.org/Benji59/PSR-15-Csrf-Middleware.svg?branch=master)](https://travis-ci.org/Benji59/PSR-15-Csrf-Middleware) [![Coverage Status](https://coveralls.io/repos/github/Benji59/PSR-15-Csrf-Middleware/badge.svg?branch=master)](https://coveralls.io/github/Benji59/PSR-15-Csrf-Middleware?branch=master)

This middleware check every POST, PUT or DELETE request for a CSRF token.
Token are persisted using an ArrayAccess compatible Session and are generated on demand.

```php
$middleware = new CsrfMiddleware($_SESSION, 200);
$app->pipe($middleware);

// Generate input
$input = "<input type=\"hidden\" name=\"{$middleware->getFormKey()}\" value=\"{$middleware->generateToken()}\"/>
```

Middleware are constructed with this parameters

- $session, **ArrayAccess|array**, used to store token
- $limit, **int**, limit the number of token to persist
- $sessionKey, **string**
- $formKey, **string**
