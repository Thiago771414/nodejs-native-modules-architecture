# Node.js Native Modules Architecture Guide

![Project Type](https://img.shields.io/badge/Project%20Type-Backend%20Architecture%20Case%20Study-purple)
![Node.js](https://img.shields.io/badge/Runtime-Node.js-green)
![JavaScript](https://img.shields.io/badge/Language-JavaScript-yellow)
![Architecture](https://img.shields.io/badge/Focus-Backend%20Fundamentals-blue)
![Modules](https://img.shields.io/badge/Concept-Native%20Modules-orange)

---

# Node.js Native Modules Architecture Guide

This repository demonstrates how core **Node.js native modules** work internally and how they can be used to build backend systems without external frameworks.

The project explores how Node.js interacts with:

- operating system resources
- network sockets
- HTTP servers
- event-driven architecture
- streams and file systems

It serves as a **backend engineering case study** for understanding Node.js fundamentals.

<p align="center">
  <img src="https://raw.githubusercontent.com/Thiago771414/imagensProjetos/main/slices/mobile/NodeNativeModules.png" width="900">
</p>

# Case Study

## Problem

Many backend developers start working with frameworks like Express or NestJS without fully understanding how Node.js works internally.

Without understanding native modules such as:

- http
- events
- stream
- dns
- net

it becomes difficult to debug performance issues or design scalable systems.

---

## Solution

This repository demonstrates how Node.js native modules can be used to build core backend functionality such as:

- HTTP servers
- event-driven systems
- DNS resolution
- OS interaction
- network sockets
- data streaming

Each example illustrates how Node.js exposes low-level system capabilities directly to JavaScript.

---

# Architecture

Example architecture using native Node.js modules:

```text
Client
│
▼
HTTP Server (http module)
│
▼
Event System (events)
│
├─ File System / Streams
│
├─ Network Layer (net)
│
├─ Domain Resolution (dns)
│
└─ System Information (os)
```


This demonstrates Node.js' **event-driven and non-blocking architecture**.

---

# Native Modules Covered

## Events Module

The **events module** provides the `EventEmitter` class used for event-driven programming.

```javascript
const { EventEmitter } = require('events');

const eventEmitter = new EventEmitter();

eventEmitter.on('bomdia', (data) => {
  console.log(`Recebi um bom dia de: ${data}`);
});

eventEmitter.emit('bomdia', 'Puc');
```
This pattern is widely used internally by Node.js.

# HTTP Module

The http module allows building web servers directly with Node.js.
```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'application/json');
  res.end('{ "user": "Fake User", "empresa": "PUC Minas" }');
});

server.listen(3000);
```
Frameworks like Express are built on top of this module.

# DNS Module

The dns module enables domain name resolution.
```js
const { Resolver } = require('dns');

const resolver = new Resolver();
resolver.setServers(['8.8.8.8']);

resolver.resolve4('pucminas.br', (err, addresses) => {
  console.log(addresses);
});
```
Used in networking and service discovery systems.

# Path Module

The path module safely manipulates filesystem paths.
```js
const path = require('path');

const filePath = '/home/user/documents/report.txt';

console.log(path.basename(filePath));
console.log(path.extname(filePath));
console.log(path.dirname(filePath));
```
Ensures compatibility across operating systems.

# OS Module

The os module provides system-level information.
```js
const os = require('os');

console.log(os.platform());
console.log(os.arch());
console.log(os.freemem());
console.log(os.totalmem());
```
Useful for monitoring and diagnostics.

# Process Module

The process module exposes information about the Node.js runtime.
```js
console.log(process.env);
console.log(process.argv);
console.log(process.pid);
console.log(process.cwd());
```
Often used in CLI tools and configuration management.

# Net Module

The net module enables TCP server and client creation.

```js
const net = require('net');

const server = net.createServer((socket) => {
  socket.write('Connection established');
  socket.end();
});

server.listen(3000);
```
This module powers many low-level networking systems.

# URL Module

The url module parses and manipulates URLs.
```js
const url = require('url');

const parsedUrl = url.parse('https://example.com/path?q=test', true);

console.log(parsedUrl.query);
```
Important for HTTP request handling.

# Stream Module

Streams allow efficient handling of large data flows.
```js
const fs = require('fs');

const readable = fs.createReadStream('input.txt');
const writable = fs.createWriteStream('output.txt');

readable.pipe(writable);
```
Streams are fundamental to Node.js performance

# Folder Structure

Example structure for the project:
```text
node-native-modules
│
├── examples
│   ├── events.js
│   ├── http-server.js
│   ├── dns.js
│   ├── streams.js
│   ├── net-server.js
│
├── README.md
│
└── package.json
```

# How to Run

Clone the repository:
```text
git clone
```
Navigate to the project:
```text
cd node-native-modules
```
Run any example:
```text
node examples/http-server.js
```

# Learning Outcomes

Developers studying this repository will understand:

Node.js event-driven architecture

native module ecosystem

HTTP server creation

network communication

streaming data processing

OS and process interaction

# Technologies

Node.js

JavaScript

TCP Networking

HTTP

Event-driven architecture

# Author

Thiago Reis Lima

LinkedIn
```text
https://www.linkedin.com/in/thiago-lima-2a5896166/
```
