# How to deploy your own cross-chain NFT

We provide the contract integrated bridge function as SDK for the users who want to create a more advanced NFT utilizing cross-chain. For example, a chain with minted NFTs, a chain with current NFTs, the itinerancy of NFT bridges, and other NFTs whose metadata changes according to these attributes, and so on, will allow for new expressions that have not been possible before!

You can create those NFTs easily by installing SDK and inheriting the contract follow the instructions in the document below.

### Installation

```
$ npm i @nfthashi/contracts
```

The functions and interfaces of each contract are summarized [here.](../sdk-guide.md)

### Usage

Once installed, you can use the contracts in the library by importing them:

When you deploy to Rinkeby, the arguments would be like these.

```
pragma solidity ^0.8.0;

import "@nfthashi/contracts/NativeHashi721.sol";

contract NativeHashi721Example is NativeHashi721 {
  uint256 private immutable _startTokenId;
  uint256 private immutable _endTokenId;
  uint256 private _supplied;

  string private _baseTokenURI;

  constructor(
    uint32 selfDomain,
    address connext,
    address dummyTransactingAssetId,
    string memory name,
    string memory symbol,
    uint256 startTokenId,
    uint256 endTokenId,
    string memory baseTokenURI
  ) NativeHashi721(selfDomain, connext, dummyTransactingAssetId, name, symbol) {
    _startTokenId = startTokenId;
    _endTokenId = endTokenId;
    _baseTokenURI = baseTokenURI;
  }

  function mint(address to) public {
    uint256 tokenId = _startTokenId + _supplied;
    require(tokenId <= _endTokenId, "NativeHashi721: mint finished");
    _mint(to, tokenId);
    _supplied++;
  }

  function tokenURI(uint256 tokenId) public view override returns (string memory) {
    return super.tokenURI(tokenId);
  }

  function _baseURI() internal view virtual override returns (string memory) {
    return _baseTokenURI;
  }
}
```

See documentation for variables required to deploy to other chains

{% hint style="info" %}
Constructor arguments

*   selfDomain

    The domain ID of the network you deploy

    You can find the ID  [here](../informations.md#domain-id)
*   connext

    The connext handler address of the network you deploy

    You can find the connext addresses  [here](../informations.md#connext-contract-address)
*   dummyTransactionAssetId

    The test ERC20 token address of the network you deploy

    You can find the Test ERC20 address  [here](../informations.md#test-erc20-contract-address)
{% endhint %}

_If you're new to smart contract development, head to_ [_Developing Smart Contracts_](https://docs.openzeppelin.com/learn/developing-smart-contracts) _to learn about creating a new project and compiling your contracts. This Openzeppelin document helps your understanding._

### Deployment

* Token ID should be different in each chain. For example, Rinkeby token ID is 0-999, and Kovan token ID is 1000-1999.
* After deploying the contract to each chain, all contract connections should be registered.
