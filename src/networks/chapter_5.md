# Network Layer

## 5.1 Network Layer Design Issues

### 5.1.1 Store and Forward Packet Switching

This section is essentially saying we're mostly concerned with the algorithms
not really care what is running them, store and forward is discussed in previous
chapter.

### 5.1.2 Services Provided to Transport Layer

The network layer provides services to the transport layer services must be designed with the following in mind:

1. Services should be independent of router technology
2. The transport layer should be shielded from number type and topology of routers present
3. The network addresses made available to the transport layer should use uniform numbering plan even across LANs and WANs

### 5.1.3 Implementation of Connectionless Service

In a connectionless service we have a datagaram network where datagrams
(telegrams with data) are sent across the network as per a connectionless
service. In a connected service we use virtual circuits (VC) where a connection
is establish for a datagram across a VC before we send the datagram

### 5.1.4 Implementation of Connection Oriented Service

For a connection oriented service we use VC network. We establish a virtual
circuit across the network from the `src` to `dest` each node stores something
in their tables and this virtual circuit is used until the connection is closed
then the virtual circuit is closed.

**TODO** finish this section there's a diagram explaining the tables and
explanation

#### 5.1.5 Comparison of VC and Datagram Networks

| **Issue** | **Datagram Network** | **Virtual-circuit Network** |
|---|---|---|
| Circuit Setup | Not needed | Required |
| Addressing | Each packet contains source and destination addresses | Each packet contains a short VC number |
| State Information | Routers do not hold state info about connections | Each VC requires router table space for each connection |
| Routing | Each packet is routed independently | Established path |
| Effect of router failures | None, except for lost packets | All VCs which pass through are broken and router is terminated |
| Quality of Service | Difficult | Easy if enough resources can be allocated |
| Congestion Control | Difficult | Easy if enough resources can be allocated |

## 5.2 Routing Algorithms

The main purpose of this layer is the problem of routing. Routing packets from
source to destination.

**forwarding** happens when a packet arrives we look up information about the
outgoing connection in the routing table as to where to send the packet and
**routing** fills and updates routing tables.

this feels like there's a lot of explanation going on but not a lot of rigorous
things that can be tested on
