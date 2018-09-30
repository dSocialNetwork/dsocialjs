# dSocial.js

A lightweight JavaScript library for dSocial

### Install
```
npm install dsocialjs --save
```

### Usage
```js
var dsocial = require('dsocialjs');

// Init WebSocket client
var client = new dsocial.Client('wss://greatchain.dpays.io');

// Get accounts
client.call('get_accounts', ['jared'], function(err, result) {
  console.log(err, result);
});
```

### Promises

You can also use dSocial.js with promises by promisifying dSocial with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var dsocial = require('dsocialjs');
bluebird.promisifyAll(dsocial.Client.prototype);
```

It'll add a *Async* to all dSocial functions (e.g. return client.callAsync().then())

```js
// So instead of writing client.request('get_accounts', ['jared'], cb); you have to write:
return client.callAsync('get_accounts', ['jared']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'jared' ...]
});
```

## License

[MIT](LICENSE).
