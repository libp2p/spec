6 Interfaces
============

`libp2p` is a collection of several protocols working together to offer a common solid interface that can talk with any other network addressable process. This is made possible by shimming currently existing protocols and implementations into a set of explicit interfaces: Peer Routing, Discovery, Stream Muxing, Transports, Connections and so on.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [6 Interfaces](#6-interfaces)
  - [6.1 libp2p](#61-libp2p)
  - [6.2 Peer Routing](#62-peer-routing)
  - [6.3 Swarm](#63-swarm)
    - [6.3.1 Transport](#631-transport)
    - [6.3.2 Connection](#632-connection)
    - [6.3.3 Stream Muxing](#633-stream-muxing)
  - [6.4 Distributed Record Store](#64-distributed-record-store)
  - [6.5 Peer Discovery](#65-peer-discovery)
  - [6.6 libp2p interface and UX](#66-libp2p-interface-and-ux)
    - [Constructing a libp2p instance programatically](#constructing-a-libp2p-instance-programatically)
    - [Dialing and Listening for connections to/from a peer](#dialing-and-listening-for-connections-tofrom-a-peer)
    - [Finding a peer](#finding-a-peer)
    - [Storing and Retrieving Records](#storing-and-retrieving-records)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 6.1 libp2p

`libp2p`, the top module that provides an interface to all the other modules that make a `libp2p` instance, must offer an interface for dialing to a peer and plugging in all of the modules (e.g. which transports) we want to support. We present the `libp2p` interface and UX in [section 6.6](#66-libp2p-interface-and-ux), after presenting every other module interface.

## 6.2 Peer Routing

![](https://raw.githubusercontent.com/libp2p/interface-peer-routing/master/img/badge.png)

A Peer Routing module offers a way for a `libp2p` `Node` to find the `PeerInfo` of another `Node`, so that it can dial that node. In its most pure form, a Peer Routing module should have an interface that takes a 'key', and returns a set of `PeerInfo`s.
See https://github.com/libp2p/interface-peer-routing for the interface and tests.

## 6.3 Swarm

Current interface available and updated at:

https://github.com/libp2p/js-libp2p-swarm#usage

### 6.3.1 Transport

![](https://raw.githubusercontent.com/libp2p/interface-transport/master/img/badge.png)

https://github.com/libp2p/interface-transport

### 6.3.2 Connection

![](https://raw.githubusercontent.com/libp2p/interface-connection/master/img/badge.png)

https://github.com/libp2p/interface-connection

### 6.3.3 Stream Muxing

![](https://github.com/libp2p/interface-stream-muxer/raw/master/img/badge.png)

https://github.com/libp2p/interface-stream-muxer

## 6.4 Distributed Record Store

![](https://raw.githubusercontent.com/libp2p/interface-record-store/master/img/badge.png)

https://github.com/libp2p/interface-record-store

## 6.5 Peer Discovery

A Peer Discovery module interface should return `PeerInfo` objects, as it finds new peers to be considered by our Peer Routing modules.

## 6.6 libp2p interface and UX

`libp2p` implementations should enable it to be instantiated programmatically, or to use a previous compiled library with some of the protocol decisions already made, so that the user can reuse or expand.

### Constructing a libp2p instance programatically

Example made with JavaScript, should be mapped to other languages:

```JavaScript
var Libp2p = require('libp2p')

var node = new Libp2p()

// add a swarm instance
node.addSwarm(swarmInstance)

// add one or more Peer Routing mechanisms
node.addPeerRouting(peerRoutingInstance)

// add a Distributed Record Store
node.addDistributedRecordStore(distributedRecordStoreInstance)
```

Configuring `libp2p` is quite straightforward since most of the configuration comes from instantiating the several modules, one at a time.

### Dialing and Listening for connections to/from a peer

Ideally, `libp2p` uses its own mechanisms (PeerRouting and Record Store) to find a way to dial to a given peer:

```JavaScript
node.dial(PeerInfo)
```

To receive an incoming connection, specify one or more protocols to handle:

```JavaScript
node.handleProtocol('<multicodec>', function (duplexStream) {

})
```

### Finding a peer

Finding a peer is done through Peer Routing, so the interface is the same.

### Storing and Retrieving Records

Like Finding a peer, Storing and Retrieving records is done through Record Store, so the interface is the same.
