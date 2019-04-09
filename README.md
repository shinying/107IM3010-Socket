# Micro Payment System

[Final Project](https://ceiba.ntu.edu.tw/course/5c74c2/hw/2018-Programming%20Assignment.pdf) of NTU IM3010 Computer Network and Application

## Introduction

A secure P2P micropayment system implmented in C++, Unix socket API and openSSL, with features including

1. Management and authentication of clients accounts on server side
2. Instant communication between clients and the server
3. Individually encrypted communication between clients and the server

## Environment

g++ 8.2.0 with C++ 11

## File Description

```
.
├── src/
|   ├── Makefile        g++ compiler make file
|   ├── client.h        client header
|   ├── client.cpp      client implementation
|   ├── server.h        server header
|   ├── server.cpp      server implementation
|   ├── util.h          utility functions for openSSL
|   ├── ThreadPool.h    thread pool implementation*
|   ├── SafeQueue.h     thread pool implementation*
|   ├── cmdParser.h     command line interface from NTU DSnP Course
|   ├── cmdCharDef.h    command line interface from NTU DSnP Course
|   ├── cmdCharDef.cpp  command line interface from NTU DSnP Course
|   └── key/            folders containg keys for encryption
├── ref.md              some tutorials about openSSL
├── flow.jpeg           the flow of the whole application
├── README.md           this file
```

\*adapted from [mtrebi](https://github.com/mtrebi/thread-pool)'s implementation

## Usage

### Compilation

```bash
make        # compile server and client
make clean  # clean files generated from compilation
make v      # print all messages and certificates
```

### Client

```bash
./client
```

#### Commands

characters in lower cases are dispensable

```text
• Connect [ip] [port]       connect to [ip]:[port] (default 127.0.0.1:8080)
• Register <name> <amount>  register a user with name <name> and balance <amount>
• LOgin <name> <port>       login with name <name> and port <port>
• Pay <user name> <amount>  pay <user name> <amount> dollars
• LIst                      list all online users
• Help                      list all available commands
• Disconnect                close the currect connection
• Ctrl-D                    disconnect and quit
```

### Server

```bash
./server
```

## Remark

First generate certificates for encryption before execution. As this application demonstrating communication between clients and a server, generate public and private keys as `caCert.pem` and `caKey.pem` for CA, `cliCert.pem` and `cliKey.pem` for client 1, `cli2Cert.pem` and `cli2Key.pem` for client 2, `servCert.pem` and `servKey.pem` for the server. Then collect all certificates in a folder `key` under `src`. See `ref.md` for reference.