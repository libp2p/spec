# libp2p specification

<h1 align="center">
  <img src="https://raw.githubusercontent.com/libp2p/libp2p/a13997787e57d40d6315b422afbe1ceb62f45511/logo/libp2p-logo.png" alt="libp2p logo"/>
</h1>

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](http://ipn.io)
[![](https://img.shields.io/badge/project-libp2p-blue.svg?style=flat-square)](http://github.com/libp2p/libp2p)
[![](https://img.shields.io/badge/freenode-%23ipfs-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23ipfs)

> This document presents `libp2p`, a modularized and extensible network stack to overcome the networking challenges faced when doing peer-to-peer applications. `libp2p` is used by IPFS as its networking library.

Authors:

- [Juan Benet](https://github.com/jbenet)
- [David Dias](https://github.com/diasdavid)

Reviewers:

- `N/A`

## Abstract

This describes the [libp2p](https://libp2p.io/) network protocol. The network layer provides point-to-point transports (reliable and unreliable) between any two libp2p nodes in the network.

This document defines the spec implemented in `libp2p`.

## Status of this spec ![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square)

## Organization of this document

This RFC is organized by chapters described on the *Table of contents* section. Each of the chapters can be found in its own file.

## Table of contents

- [1 Introduction](1-introduction.md)
  - [1.1 Motivation](1-introduction.md#11-motivation)
  - [1.2 Goals](1-introduction.md#12-goals)
- [2 An analysis the state of the art in network stacks](2-state-of-the-art.md)
  - [2.1 The client-server model](2-state-of-the-art.md#21-the-client-server-model)
  - [2.2 Categorizing the network stack protocols by solutions](2-state-of-the-art.md#22-categorizing-the-network-stack-protocols-by-solutions)
  - [2.3 Current shortcomings](2-state-of-the-art.md#23-current-shortcomings)
- [3 Requirements](3-requirements.md)
  - [3.1 Transport agnostic](3-requirements.md#34-transport-agnostic)
  - [3.2 Multi-multiplexing](3-requirements.md#35-multi-multiplexing)
  - [3.3 Encryption](3-requirements.md#33-encryption)
  - [3.4 NAT traversal](3-requirements.md#31-nat-traversal)
  - [3.5 Relay](3-requirements.md#32-relay)
  - [3.6 Enable several network topologies](3-requirements.md#36-enable-several-network-topologies)
  - [3.7 Resource discovery](3-requirements.md#37-resource-discovery)
  - [3.8 Messaging](3-requirements.md#38-messaging)
  - [3.9 Naming](3-requirements.md#38-naming)
- [4 Architecture](4-architecture.md)
  - [4.1 Peer Routing](4-architecture.md#41-peer-routing)
  - [4.2 Swarm](4-architecture.md#42-swarm)
  - [4.3 Distributed Record Store](4-architecture.md#43-distributed-record-store)
  - [4.4 Discovery](4-architecture.md#44-discovery)
  - [4.5 Messaging](4-architecture.md#45-messaging)
    - [4.5.1 PubSub](4-architecture.md#451-pubsub)
  - [4.6 Naming](4-architecture.md#46-naming)
    - [4.6.1 IPRS](4-architecture.md#461-iprs)
    - [4.6.2 IPNS](4-architecture.md#462-ipns)
- [5 Data structures](5-datastructures.md)
- [6 Interfaces](6-interfaces.md)
  - [6.1 libp2p](6-interfaces.md#61-libp2p)
  - [6.1 Transport](6-interfaces.md)
  - [6.2 Connection](6-interfaces.md)
  - [6.3 Stream Multiplexer](6-interfaces.md)
  - [6.3 Swarm](6-interfaces.md#63-swarm)
  - [6.5 Peer Discovery](6-interfaces.md#65-peer-discovery)
  - [6.2 Peer Routing](6-interfaces.md#62-peer-routing)
  - [6.2 Content Routing](6-interfaces.md#62-peer-routing)
    - [6.3.1 Distributed Record Store](6-interfaces.md#64-distributed-record-store)
  - [6.6 libp2p interface and UX](6-interfaces.md#66-libp2p-interface-and-ux)
- [7 Properties](7-properties.md)
  - [7.1 Communication Model - Streams](7-properties.md#71-communication-model---streams)
  - [7.2 Ports - Constrained Entrypoints](7-properties.md#72-ports---constrained-entrypoints)
  - [7.3 Transport Protocol](7-properties.md#73-transport-protocols)
  - [7.4 Non-IP Networks](7-properties.md#74-non-ip-networks)
  - [7.5 On the wire](7-properties.md#75-on-the-wire)
    - [7.5.1 Protocol-Multiplexing](7-properties.md#751-protocol-multiplexing)
    - [7.5.2 multistream - self-describing protocol stream](7-properties.md#752-multistream---self-describing-protocol-stream)
    - [7.5.3 multistream-selector - self-describing protocol stream selector](7-properties.md#753-multistream-selector---self-describing-protocol-stream-selector)
    - [7.5.4 Stream Multiplexing](7-properties.md#754-stream-multiplexing)
    - [7.5.5 Portable Encodings](7-properties.md#755-portable-encodings)
    - [7.5.6 Secure Communications](7-properties.md#756-secure-communications)
- [8 Implementations](8-implementations.md)
- [9 References](9-references.md)

## Other specs that haven't made to the main document

- [Relay](/relay)
- [PubSub](/pubsub)

## Contribute

Please contribute! [Dive into the issues](https://github.com/libp2p/specs/issues)!

Please be aware that all interactions related to multiformats are subject to the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

## License

[CC-BY-SA 3.0 License](https://creativecommons.org/licenses/by-sa/3.0/us/) © Protocol Labs Inc.
