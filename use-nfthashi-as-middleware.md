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
| Ethereum Georli | 0x03eC62c5F5FC375bFB373014C9D4be109Dcc15e8 | 1735353714 |
| Optimism Georli | 0x368888035172f48896F975C8ef8b640FF1b1dAf8 | 1735356532 |
| Polygon Mumbai  | 0x0c4005681B59d5B9A42BD60665a936a643294F60 | 9991       |

### Smart Contract Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

interface IHashi721Bridge {
  function xCall(
    uint32 destination,
    uint256 relayerFee,
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
        address asset,              // NFT contract address
        address to,                 // NFT receiver in destination chain
        uint256 tokenId,            // NFT token ID
        bool isTokenURIIgnored   // if token URI is not required, set true
    ) public {
        // specific logic for your dApp
        IHashi721Bridge(nftHashiBridgeContract).xCall(destination, relayerFee, asset, to, tokenId, isTokenURIIgnored);
    }
}
```

### Interact from frontend

The user must approve the NFTHashi bridge contract to transfer NFT before calling.&#x20;



