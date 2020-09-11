# Streams overview

**Streams is a framework for building cryptographic messaging protocols in the [Rust programming language](https://www.rust-lang.org/). Streams comes with a built-in protocol for attaching messages to the Tangle, but it's also flexible enough to allow you to extend it to send messages in other ways such as in HTTP URLs.**

Here are just a few ideas of what you can build with Streams:

- An API service that encrypts data if it's behind a paywall
- A marketing subscription service that keeps an auditible record of subscriptions in the Tangle
- A secure messaging protocol that relies on cryptographic keys to identify users

<iframe width="560" height="315" src="https://www.youtube.com/embed/jDCMuML1QBo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Limitations

Messages are intended to be read and processed. After a message is sent, you should not rely on being able to read that message again.

## Supported languages

### **Official support** ###

---------------
#### **Rust** ####
[Link](guides/building-a-protocol.md)
---------------

## Roadmap

Streams is in the alpha phase of the release cycle. The purpose of this version of Streams is to get some feedback before we progress towards the final implementation.

See the [roadmap](https://roadmap.iota.org/masked-authenticated-messaging-v1_1) for more information.

## Blog posts

---------------
#### **IOTA Streams Alpha** ####
[IOTA Streams Alpha](https://blog.iota.org/iota-streams-alpha-7e91ee326ac0)

An overview of the alpha release of Streams.
---------------

## Source code

The source code for this project is hosted on [Github](https://github.com/iotaledger/streams).

## Next steps

Take a look at how to [build a Streams protocol](guides/building-a-protocol.md).

