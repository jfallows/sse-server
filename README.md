[![view on npm](https://badgen.net/npm/v/sse-server)](https://www.npmjs.org/package/sse-server)
[![npm module downloads](https://badgen.net/npm/dt/sse-server)](https://www.npmjs.org/package/sse-server)
[![Gihub repo dependents](https://badgen.net/github/dependents-repo/75lb/sse-server)](https://github.com/75lb/sse-server/network/dependents?dependent_type=REPOSITORY)
[![Gihub package dependents](https://badgen.net/github/dependents-pkg/75lb/sse-server)](https://github.com/75lb/sse-server/network/dependents?dependent_type=PACKAGE)
[![Build Status](https://travis-ci.org/75lb/sse-server.svg?branch=master)](https://travis-ci.org/75lb/sse-server)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/feross/standard)

# sse-server

Pipe an event stream from terminal to browser.

## Synopsis

To generate the certificate and key.

```bash
openssl req -x509 -newkey rsa:2048 -nodes -sha256 -subj '/CN=localhost' \
  -keyout localhost-privkey.pem -out localhost-cert.pem
```

Launch the server.

```
$ sse-server -k ./localhost-privkey.pem -c localhost-cert.pem
SSE server: https://localhost:9000 
Input socket: localhost:9090
```

Pipe events to the input socket.

```
$ echo '{ "name": "something", "data": "one" }' | nc -c localhost 9090
$ echo '{ "name": "something", "data": "two" }' | nc -c localhost 9090
```

Connect a browser to the SSE server to consume the [server-sent events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events).

```
$ curl -k https://localhost:9000
event: something
data: "one"

event: something
data: "two"
```

* * *

&copy; 2018-21 Lloyd Brookes \<75pound@gmail.com\>.
