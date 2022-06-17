# Architecture

We use Connext, and Connext provides trust-minimized cross-chain messaging using optimistic verification provided by Nomad, the most trust-minimized protocol for cross-chain messaging.

#### Why is trust minimized? <a href="#why-is-trust-minimized" id="why-is-trust-minimized"></a>

Connext is built on an optimistic communication protocol that requires only 1 good actor in the space to remain secure. This is the most trust minimized solution currently available beyond native bridges (Ethereum-L2s, IBC) that are not available across separate domains.

#### How it works: <a href="#how-it-works" id="how-it-works"></a>

A message is passed by a relayer between 2 chains but, before it becomes valid, there is a 30 minutes latency period. During this time any watcher can prove that the message is invalid and slash it. It’s a fraud-proof system of optimistic rollups.

For more information, see this article\
[https://blog.connext.network/optimistic-bridges-fb800dc7b0e0](https://blog.connext.network/optimistic-bridges-fb800dc7b0e0)



### Contract Construction

NFTHashis supports any NFTs already created. A simple ERC721 contract is deployed on the bridged chain based on the information of the original NFT existing in Chain A (Origin Chain) and minted to the address that caused the Tx. In case of unwrapping from Chain B to Chain A, a wrapped NFT on Chain B will be burned, and an NFT deposited in contract on Chain A will be transferred to the owner on Chain B on Chain A.

Let me describe along with the user flow.

#### Case of bridge from Chain A to Chain B：Wrap

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.44.36.png>)

* Deposit an NFT to NFT Hashi handler contract on Chain A (Origin Chain)
* The handler contract sends the information of NFT or chains to Chain B using xCall supported by Connext. (more info about xCall ⇒ [xapp-starter](https://github.com/connext/xapp-starter)
* The Handler Contract of Chain B receives the xCall from Chain A
* Compute the contract address from the information of these using Create2.
* If the computed address has not been deployed, the wrapped NFT contract is deployed to the computed contract address and minted. After the second time, the NFT is minted from a contract that has already been deployed.



#### Case of bridge from Chain B to Chain A: Unwrap

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.46.09.png>)

* The bridge contract burns the wrapped NFT minted on Chain B
* Refer to the mapping of Chain A address and Chain B address
* Send NFT information to Chain A using xCall
* The Handler Contract of Chain B receives the xCall from Chain A
* An NFT deposited in contract with Chain A will be transferred to the address of an owner at Chain B



### NativeNFTHashi

In the case of using our SDK, the architecture is different from the main architecture.

This is the bridge function for users trying to create the new NFT project with the cross-chain bridge. We develop a contract that incorporates the cross-chain bridge function to ERC721. You can use A as is or inherit it and create a contract to support a cross-chain NFT bridge.

### Bridge Mechanism

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.51.20.png>)

* Every time a new chain is supported, you must do this process
* Call xSend function in \<NativeBridgeContractName>. This is a function to bridge NFT
* In chain A, NFT will be burned and the information of NFT or chains are sent to Chain B using xCall
* Chain B receive xCall from ChainA, and mint the NFT on Chain B to the owner on ChainA
* When bridging from Chain B to another chain, in the same way, burned at the origin chain and minted at destination chain.



### Initialization Requirement

Some initial setup is required when using the NFTs with the bridge function

*   Deploy

    NFTHashi Native contract must be deployed to all chains you wand to support
*   Resister

    In order for NativeHashi721 of different chains to recognize them as NativeHashi721 of the same project, the mapping of the chain's domain ID to the contract address must be registered in the NativeHashi721 of each chain

Detailed initial setup instructions are provided in the Dev Guide

* [Deployment](broken-reference)
* [Resister](broken-reference)
