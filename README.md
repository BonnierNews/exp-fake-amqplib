## exp-fake-amqplib

Mocked version of https://www.npmjs.com/package/amqplib.
Currently only supports the callback API.

### Overriding amqplib

You might want to override `amqplib` with `exp-fake-amqplib` in tests. This can be done this way:

```javascript
const amqplib = require("amqplib");
const fakeAmqplib = require("exp-fake-amqplib");

amqplib.connect = fakeAmqp.connect;
```

If you are using version 2 or higher of [exp-amqp-connection](https://www.npmjs.com/package/exp-amqp-connection)
you can use [proxyquire](https://www.npmjs.com/package/proxyquire) to replace `amqplib` with `exp-fake-amqplib` in your tests like this:

```javascript
const fakeAmqp = require("exp-fake-amqplib");

proxyquire("exp-amqp-connection/bootstrap", {
  "amqplib/callback_api": fakeAmqp
});
```
