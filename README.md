# Overview

NFTHashi is a Trust-minimized crosschain NFT bridge built with [Connext](https://www.connext.network).

[https://nfthashi.com/](https://nfthashi.com/)

<figure><img src=".gitbook/assets/Screen Shot 2022-11-21 at 22.02.19.png" alt=""><figcaption><p>NFTHashi</p></figcaption></figure>

### Motivation

NFTHashi team wants to provide a general & trust-minimized cross-chain bridge for NFT.\
\
NFTHashi brings&#x20;

### How it works

<figure><img src=".gitbook/assets/xNFTs Mindmap.jpg" alt=""><figcaption><p>How it works</p></figcaption></figure>

NFTHashi uses Connext as an internal cross-chain messaging protocol.

The workflow of the bridge is the following.

1. A User deposits NFT in the NFTHashi at the source chain
2. The NFTHashi makes a cross-chain call through Connext
3. The NFTHashi receives a cross-chain message in the destination chain
4. The NFTHashi mint corresponding NFT to the user in the destination chain

### Brided Information

* The contract address is calculated from the NFT original contract address and chain. It uses create2, so the address in the destination chain is calculated counterfactually.
* Token ID is the same for both the source chain and the destination chain
* Token URI is copied and bridged to the destination chain

### Security Concerns

* NFTHashi leverages Connext, so we have the same security model as Connext.
* NFTHashi uses Lock & Mint model in the bridge. And NFTHashi team has an upgradability role in the contract in the early time. This is an additional trusting point on top of Connext.

### Team

NFTHashi project starts from [ETHAmsterdam](https://blog.connext.network/ethamsterdam-connext-hackathon-winners-95f4259fb675) hackathon

### Community

Please contact us at [NFTHashi Discord](https://discord.gg/CJunM9EUw9)
