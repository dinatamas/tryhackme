Network Services 2
==================

Enumerating and Exploiting More Common Network Services & Misconfigurations.

## 1. Get Connected

### (1)

_Ready? Let's get going!_

>  N/A

## 2. Understanding NFS

- NFS: Network File System protocol.
- Mount file system on a server, then client mounts it locally.
- https://docs.oracle.com/cd/E19683-01/816-4882/6mb2ipq7l/index.html
- Local mount service -> RPC call -> NFSD daemon.
  - Returns the unique file handlers.
  - Permission control (users / groups).

### (1)

_What does NFS stand for?_

> Network File System

### (2)

_What process allows an NFS client to interact with a remote
directory as though it was a physical device?_

> mounting

### (3)

_What does NFS use to represent files and directories on the server?_

> file handler

### (4)

_What protocol does NFS use to communicate between the server and client?_

> rpc

### (5)

_What two pieces of user data does the NFS server take as parameters for
controlling user permissions? Format: parameter 1 / parameter 2_

> user id / group id

### (6)

_Can a Windows NFS server share files with a Linux client? (Y/N)_

> Y

### (7)

_Can a Linux NFS server share files with a MacOS client? (Y/N)_

> Y

### (8)

_What is the latest version of NFS? [released in 2016, but is still up to date as of 2020]
This will require external research._

See: RFC7862

> 4.2

## 3. Enumerating NFS

- Enumeration: a process which establishes an active connection to the
  target hosts to discover potential attack vectors in the system, and
  the same can be used for further exploitation of the system.
  - Infosec Institute topics
