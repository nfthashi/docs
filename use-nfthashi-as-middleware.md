# Use NFTHashi as middleware

You can integrate NFTHashi smart contracts into your contracts.

### Overview

You can integrate the NFTHashi contract using the following interface and deployed contract addresses.

### Interface

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

interface IHashi721Bridge {
  function xCall(
    uint32 destination,
    uint256 relayerFee,
    uint256 slippage,
    address asset,
    address to,
    uint256 tokenId,
    bool isTokenURIIgnored
  ) external payable returns (bytes32);
}
```

### Deployments

#### Mainnet

TBD

#### Testnet

| Network         | Address                                    | Domain ID  |
| --------------- | ------------------------------------------ | ---------- |
| Ethereum Georli | 0x8F5969b8Fa3727392385C5E74CF1AA91a4aC4b40 | 1735353714 |
| Optimism Georli | 0xb8336251667A3c73faA7e646d3686596069c9D1C | 1735356532 |
| Polygon Mumbai  | 0xd3F1A0782AFD768f8929343Fb44344A2a49fE343 | 9991       |

### Smart Contract Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

interface IHashi721Bridge {
  function xCall(
    uint32 destination,
    uint256 relayerFee,
    uint256 slippage,
    address asset,
    address to,
    uint256 tokenId,
    bool isTokenURIIgnored
  ) external payable returns (bytes32);
}

contract SampleXApp {
    address nftHashiBridgeContract;
    
    constructor(address _nftHashiBridgeContract) {
        nftHashiBridgeContract = _nftHashiBridgeContract;
    }
    
    function sampleXCall(    
        uint32 destination,         // domain ID from above list
        uint256 relayerFee,         // check Connext document
        uint256 slippage,           // check Connext document
        address asset,              // NFT contract address
        address to,                 // NFT receiver in destination chain
        uint256 tokenId,            // NFT token ID
        uint256 isTokenURIIgnored   // if token URI is not required, set true
    ) public {
        // specific logic for your dApp
        IHashi721Bridge(nftHashiBridgeContract).xCall(destination, relayerFee, slippage, asset, to, tokenId, isTokenURIIgnored);
    }
}
```

### Interact from frontend

The user must approve the NFTHashi bridge contract to transfer NFT before calling.&#x20;



