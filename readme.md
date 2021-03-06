<img style="width: 100%; max-width: 400px;" src="http://feathersjs.com/img/feathers-logo-wide.png" alt="Feathers logo">

## A REST and realtime API layer for modern applications.

[![Build Status](https://travis-ci.org/feathersjs/feathers.png?branch=master)](https://travis-ci.org/feathersjs/feathers)
[![Dependency Status](https://img.shields.io/david/feathersjs/feathers.svg?style=flat-square)](https://david-dm.org/feathersjs/feathers)

[![Greenkeeper badge](https://badges.greenkeeper.io/feathersjs/feathers.svg)](https://greenkeeper.io/)
[![Maintainability](https://api.codeclimate.com/v1/badges/cb5ec42a2d0cc1a47a02/maintainability)](https://codeclimate.com/github/feathersjs/feathers/maintainability)
[![Test Coverage](https://api.codeclimate.com/v1/badges/cb5ec42a2d0cc1a47a02/test_coverage)](https://codeclimate.com/github/feathersjs/feathers/test_coverage)
[![Download Status](https://img.shields.io/npm/dm/feathers.svg?style=flat-square)](https://www.npmjs.com/package/feathers)
[![Slack Status](http://slack.feathersjs.com/badge.svg)](http://slack.feathersjs.com)

Feathers is a real-time, micro-service web framework for NodeJS that gives you control over your data via RESTful resources, sockets and flexible plug-ins.

## Getting started

You can build your first real-time and REST API in just 4 commands:

```bash
$ npm install -g @feathersjs/cli
$ mkdir my-new-app
$ cd my-new-app/
$ feathers generate app
$ npm start
```

To learn more about Feathers visit the website at [feathersjs.com](http://feathersjs.com) or jump right into [the Feathers docs](http://docs.feathersjs.com).

## See it in action

Here is all the code you need to create a RESTful, real-time message API that uses an in-memory data store:

```js
// app.js
const feathers = require('@feathersjs/feathers');
const express = require('@feathersjs/express')
const socketio = require('@feathersjs/socketio');
const handler = require('@feathersjs/errors/handler');

const memory = require('feathers-memory');

// Create a Feathers application that is also fully compatible
// with an Express app
const app = express(feathers());

// Parse HTTP JSON bodies
app.use(express.json());
// Parse URL-encoded params
app.use(express.urlencoded({ extended: true }));
// Add REST API support
app.configure(express.rest());
// Configure Socket.io real-time APIs
app.configure(socketio());
// Register our memory "messages" service
app.use('/messages', memory());
// Register a nicer error handler than the default Express one
app.use(handler());
// Start the server
app.listen(3030);

// Create a new message on the server
app.service('messages').create({
  text: 'This is a test message'
});
```

Then run

```
npm install @feathersjs/feathers @feathersjs/express @feathersjs/socketio @feathersjs/errors feathers-memory
node app
```

and go to [http://localhost:3030/messages](http://localhost:3030/messages). That's it! There's a lot more you can do with Feathers including; using a real database, authentication, authorization, clustering and more! Head on over to [the Feathers docs](http://docs.feathersjs.com) to see just how easy it is to build scalable real-time apps.

## Documentation

The [Feathers docs](http://docs.feathersjs.com) are loaded with awesome stuff and tell you every thing you need to know about using and configuring Feathers.

## Examples

Each plugin has it's own minimal example in the repo. To see a more complex example go to [feathersjs/feathers-chat](https://github.com/feathersjs/feathers-chat).

## Security

We :heart: the community and take security very seriously. No one wants their app hacked. If you have come across a security concern please [report it responsibly](https://docs.feathersjs.com/security#where-should-i-report-security-issues). Visit the [Security section](https://docs.feathersjs.com/SECURITY.html) of the docs to learn more about how you can make sure your app is secure.

## Long Term Support Schedule

We are going to be following along with the Node.js long term support cycle. As a result **we have dropped official support for node v0.10, v0.12, and iojs versions**. Feathers still works on those versions but we're not going to ensure it will going forward.

We will be supporting Node.js v4 until **2018-04-01**.
We will be supporting Node.js v6 until **2019-04-18**.

## License

[MIT](LICENSE)

## Authors

[Feathers contributors](https://github.com/feathersjs/feathers/graphs/contributors)
