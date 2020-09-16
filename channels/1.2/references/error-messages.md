# Error messages

**This topic helps you understand and resolve errors that you may see while using Channels.**

## Authenticity is violated, bad signature

You may see this error if a signed message contains an invalid signature.

## Link not found

You may see this error if you're trying to process a message before having processed the message that it's linked to.

See [Linking messages](../guides/linking-messages.md) for more information.

## More than one message found

You may see this error when trying to use the `iota_client` object to receive a message on a channel when other copies of that message exist.

To resolve this error, you could do one of the following:

- Iterate over each message and handle each of them
- Use only the first valid message
- Ignore all messages when duplicates exist 

## Provided hashes are not valid: []

You may see this error if the Channels messages are sent in an inconsistent bundle.

If you see this message please reach out to us in the #streams-discussion on [Discord](https://discord.iota.org/).

## No Author's MSS public key found

You may see this error when trying to process a message that relies on information in an `Announce` message.

To resolve this error, you first need to process these messages by using the `unwrap_announcement()` method to add the channel information to the subscriber's [state](../how-it-works.md#states).

See [Linking messages](../guides/linking-messages.md) for more information.

## Can't see your error message?

Get in touch with us on [Discord](https://discord.iota.org/) in the #streams-discussion channel, or [create an issue](https://github.com/iotaledger/documentation/issues/new/choose) on GitHub.

