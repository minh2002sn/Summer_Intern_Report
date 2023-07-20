# **Report Linux Programming**
## **1. Sockets**
### **1.1. Overview**
Sockets are a method of iter-process communication (IPC) that allow data to be exchanged between applications, either on the same host (computer) or on different hosts connected by a network.

In a typical client-server scenario, applications communicate using sockets as follows:
- Each application creates a socket. A socket is the “apparatus” that allows communication, and both applications require one.
- The server binds its socket to a well-known address (name) so that clients can locate it.

A socket is created using the socket() system call, which returns a file descriptor used to refer to the socket in subsequent system calls:
```c
fd = socket(domain, type, protocol);
```

**Communication domains:**

Sockets exist in a communication domain, which determines:
- The method of identifying a socket (i.e., the format of a socket “address”).
- The range of communication (i.e., either between applications on the same host or between applications on different hosts connected via a network).

Modern operating systems support at least the following domains:
- The *UNIX* (AF_UNIX) domain allows communication between applications on the same host. (POSIX.1g used the name AF_LOCAL as a synonym for AF_UNIX, but
this name is not used in SUSv3.)
- The *IPv4* (AF_INET) domain allows communication between applications running on hosts connected via an Internet Protocol version 4 (IPv4) network.
- The *IPv6* (AF_INET6) domain allows communication between applications running on hosts connected via an Internet Protocol version 6 (IPv6) network. Although IPv6 is designed as the successor to IPv4, the latter protocol is currently still the most widely used.

|Domain  |Communication performed    |Communication between applications |Address format |Address structure  |
|:---------:|:---------:|:---------:|:---------:|:---------:|
|AF_UNIX    |within kernel  |on same host   |pathname   |sockaddr_un    |
|AF_INET    |via IPv4       |on hosts connected via IPv4 network    |32-bit IPv4 address and 16-bit port number |sockaddr_in    |
|AF_INET6   |via IPv6       |on hosts connected via IPv6 network    |128-bit IPv6 address and 16-bit port number |sockaddr_in6  |

**Socket types:**

Every sockets implementation provides at least two types of sockets: *stream* (SOCK_STREAM) and *datagram* (SOCK_DGRAM).

|Properties |Stream socket type    |Datagram socket type|
|:---------:|:---------:|:---------:|
|Realiable delivery         |Yes|No|
|Message boundaries reserved|No |Yes|
|Connection-oriented        |Yes|No|

**Socket protocol:**

The protocol parameter specifies a particular protocol to be used with the socket. In most cases, a single protocol exists to support a particular type of socket in a particular addressing family. If the protocol parameter is set to 0, the system selects the default protocol number for the domain and socket type requested. The default protocol for stream sockets is TCP. The default protocol for datagram sockets is UDP.

### **1.2. Socket address structures**


## . Process and thread

