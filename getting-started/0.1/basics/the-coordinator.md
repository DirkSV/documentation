# The Coordinator

**The Coordinator is an application that's run by the IOTA Foundation and whose purpose is protect the [Tangle](../basics/the-tangle.md) from attacks such as [parasite chains](https://blog.iota.org/attack-analysis-the-simple-parasite-chain-42a34bfeaf23). [Nodes](../basics/nodes.md) use the Coordinator to reach a consensus on which transactions are confirmed.**

## Milestones

All nodes in the same [IOTA network](../references/iota-networks.md) are hard-coded with the [address](../basics/addresses.md) of a Coordinator.

To prove to nodes that it owns the address, the Coordinator creates, signs, and sends [bundles](../basics/bundles.md) of transactions called milestones at regular intervals.

These bundles contain the following:

- Enough zero-value transactions that contain the fragmented signature
- One transaction whose [`signatureMessageFragment` field](../basics/transactions.md#signatureMessageFragment) contains enough missing data from the Merkle tree to be able to rebuild it

When a transaction in a valid milestone references an existing transaction in the Tangle, nodes mark the state of that existing transaction and its entire history as confirmed.

![Milestones being attached to the Tangle](../images/milestones.gif)

## The Coordinator's Merkle tree

Because signatures prove ownership of an address and IOTA uses one-time signatures, the Coordinator needs a way to prove to nodes that it owns an address without signing bundles with the same private key every time.

To do so, the Coordinator's address is derived from a [Merkle tree](https://en.wikipedia.org/wiki/Merkle_tree), where the address is the root, and the private keys are the leaves.

## How the Merkle tree is generated

To generate the Merkle tree, first a number of addresses and private keys are generated from the Coordinator's seed.

The total number of addresses that are generated depends on the depth of the Merkle tree: 2<sup>depth</sup>. In this example, the Merkle tree's depth is 2 because we have 4 leaves, which each represent an address.

![Example Merkle tree](../images/merkle-tree-example.png) 

:::info:
On the Mainnet, the Coordinator's Merkle tree has a depth of 23. So, the Coordinator has 8,388,608 private keys and can use each one to sign a bundle.
:::

To generate the Coordinator's address, the leaves are hashed in pairs:

- **Node 1:** Hash(Hash(leaf 1) Hash(leaf 2))
- **Node 2:** Hash(Hash(leaf 3) Hash(leaf 4))
- **Coordinator's address:** Hash(Hash(node 1) Hash(node 2))

Node 1 is a hash of the result of hashing leaf 1 and leaf 2. Node 2 is a hash of the result of hashing leaf 3 and leaf 4. The Coordinator's address is a hash of the result of hashing the hash of node 1 and node 2.

### How nodes verify milestones

When nodes see a transaction that's been sent from the Coordinator's address, they validate it by doing the following:

- Make sure that it doesn't lead to a double-spend
- Verify its signature

![Example Merkle tree](../images/merkle-tree-example.png)

To verify the signature, nodes use the information in the milestones to rebuild the Merkle tree and find the Merkle root. If the rebuilt Merkle root is the same as the Coordinator's address, nodes know the milestone was sent by the Coordinator.

For example, as a node, we have seen a bundle that was signed with the private key of leaf 1.

First, we [validate the signature](../basics/signatures.md#how-nodes-validate-signatures) to find out the address in leaf 1.

To help us calculate the Merkle root, one of the milestones in the bundle contains the following:

- The address in leaf 2
- The hash in node 2

Now, we hash the addresses in leaves 1 and 2 to find the hash in node 1. Then, we hash the hash in nodes 1 and 2 to find the Merkle root.

If the Merkle root is the same as the Coordinator's address, the bundle was signed with one of the private keys in the Coordinator's Merkle tree.

## Coordicide

The Research Department at the IOTA Foundation is focused on a project called [Coordicide](https://coordicide.iota.org/), which is a proposal for the removal of the Coordinator. When this happens, nodes will be able to reach a consensus without milestones.