# kahlys/proxy

[![godoc](https://godoc.org/github.com/kahlys/proxy?status.svg)](https://godoc.org/github.com/kahlys/proxy)
[![build](https://api.travis-ci.org/kahlys/proxy.svg?branch=master)](https://travis-ci.org/kahlys/proxy)
[![go report](https://goreportcard.com/badge/github.com/kahlys/proxy)](https://goreportcard.com/report/github.com/kahlys/proxy)

Simple tcp proxy package and executable binary in Golang.

:warning: This code is for test purpose, it is sometimes ugly, it is not production ready, and the API will probably change. :warning:

## Installation

With a correctly configured [Go toolchain](https://golang.org/doc/install):

```sh
$ git clone github.com/kahlys/proxy/
$ cd proxy
$ go install cmd/tcpproxy/*.go
```

## Example

The example executable provides both TCP and TCP/TLS connection: `cmd/tcpproxy/main.go`

By default, the proxy address is _localhost:4444_ and the target address is _localhost:80_.

```sh
$ tcpproxy
2018/12/13 17:10:25 Proxying from :4444 to :80
```

You can specify some options.

```sh
$ tcpproxy -help
Usage of tcpproxy:
  -lcert string
        certificate file for proxy server side
  -lhost string
        proxy local address (default ":4444")
  -lkey string
        key x509 file for proxy server side
  -ltls
        tls/ssl between client and proxy, you must set 'lcert' and 'lkey'
  -rcert string
        certificate file for proxy client side
  -rhost string
        proxy remote address (default ":80")
  -rkey string
        key x509 file for proxy client side
  -rtls
        tls/ssl between proxy and target, you must set 'rcert' and 'rkey'
```

## Proxy logging

Output log

```
=============================== New Seq ===============================
HTTP/1.1 200 OK
Server: Proxy
Content-Encoding: gzip
Content-Type: application/json; charset=UTF-8
Date: Sun, 30 Jan 2022 10:42:34 GMT
Content-Length: 64
...
```

Log file

```
1643539215370834000.txt
1643539277472175000.txt
1643539282064055000.txt
...
```
