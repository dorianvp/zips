
    ZIP: XXX
    Title: Deployment of the NU7 Network Upgrade
    Owners: Arya <arya@zfnd.org>
    Status: Draft
    Category: Consensus / Network
    Created: 2024-10-31
    License: MIT
    Discussions-To: <https://github.com/zcash/zips/issues/839>


# Terminology

The key word "MUST" in this document is to be interpreted as described in
BCP 14 [^BCP14] when, and only when, it appears in all capitals.

The term "network upgrade" in this document is to be interpreted as described
in ZIP 200. [^zip-0200]

The character § is used when referring to sections of the Zcash Protocol
Specification. [^protocol]

The terms "Mainnet" and "Testnet" are to be interpreted as described in
§ 3.12 ‘Mainnet and Testnet’. [^protocol-networks]


# Abstract

This proposal defines the deployment of the NU7 network upgrade.


# Specification

## NU7 deployment

The primary sources of information about NU7 consensus protocol changes are:

* The Zcash Protocol Specification [^protocol].
* ZIP 200: Network Upgrade Mechanism [^zip-0200].

The network handshake and peer management mechanisms defined in ZIP 201
[^zip-0201] also apply to this upgrade.

The following network upgrade constants [^zip-0200] are defined for the
NU7 upgrade:

CONSENSUS_BRANCH_ID
: `0x77190AD8`

ACTIVATION_HEIGHT (NU7)
: Testnet: TBD
: Mainnet: TBD

MIN_NETWORK_PROTOCOL_VERSION (NU7)
: Testnet: `170150`
: Mainnet: `170160`

For each network (Testnet and Mainnet), nodes compatible with NU7 activation
on that network MUST advertise a network protocol version that is greater
than or equal to the MIN_NETWORK_PROTOCOL_VERSION (NU7) for that activation.

## Backward compatibility

Prior to the network upgrade activating on each network, NU7 and pre-NU7
nodes are compatible and can connect to each other. However, NU7 nodes will
have a preference for connecting to other NU7 nodes, so pre-NU7 nodes will
gradually be disconnected in the run up to activation.

Once the network upgrades, even though pre-NU7 nodes can still accept the
numerically larger protocol version used by NU7 as being valid, NU7 nodes
will always disconnect peers using lower protocol versions.


# References

[^BCP14]: [Information on BCP 14 — "RFC 2119: Key words for use in RFCs to Indicate Requirement Levels" and "RFC 8174: Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words"](https://www.rfc-editor.org/info/bcp14)

[^protocol]: [Zcash Protocol Specification, Version 2024.5.1 or later](protocol/protocol.pdf)

[^protocol-networks]: [Zcash Protocol Specification, Version 2024.5.1 [NU6]. Section 3.12: Mainnet and Testnet](protocol/protocol.pdf#networks)

[^zip-0200]: [ZIP 200: Network Upgrade Mechanism](zip-0200.rst)

[^zip-0201]: [ZIP 201: Network Peer Management for Overwinter](zip-0201.rst)
