# Native Pattern

### Native Support

Native Support Pattern is the bridge function for users trying to create the new NFT project with the cross-chain bridge. We develop a contract that incorporates the cross-chain bridge function to ERC721. You can use A as is or inherit it and create a contract to support a cross-chain NFT bridge.



### Initialization Requirement

Some initial setup is required when using the NFTs with the bridge function

*   Deploy

    xNFTNative contract must be deployed to all chains you wand to support
*   Resister

    In order for xNativeNFTs of different chains to recognize them as xNativeNFTs of the same project, the mapping of the chain's domain ID to the contract address must be registered in the xNativeNFT of each chain

Detailed initial setup instructions are provided in the Dev Guide

* [Deployment](../../developer-guide/how-to-deploy-your-own-xnativenft.md#deployment)
* [Resister](../../developer-guide/how-to-deploy-your-own-xnativenft.md#register)

### Bridge Mechanism

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.51.20.png>)

* Every time a new chain is supported, you must do this process
* Call xSend function in \<NativeBridgeContractName>. This is a function to bridge NFT
* In chain A, NFT will be burned and the information of NFT or chains are sent to Chain B using xCall
* Chain B receive xCall from ChainA, and mint the NFT on Chain B to the owner on ChainA
* When bridging from Chain B to another chain, in the same way, burned at the origin chain and minted at destination chain.
