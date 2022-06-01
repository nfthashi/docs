# How to use SDK

### Installation

```
$ npm i @nfthashi/contracts
```



### Usage

Once installed, you can use the contracts in the library by importing them:

When you deploy to Rinkeby, the arguments would be like these.

```
pragma solidity ^0.8.0;

import "@nfthashi/contracts/contracts/native/NFTNativeBridge.sol";

contract MyNFT is NFTNativeBridge{
    constructor() NFTNativeBridge( .  
        1111,                                         /selfDomain ID
        0x2307Ed9f152FA9b3DcDfe2385d279D8C2A9DF2b0,   /Connext handler address
        0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9 .  /dummyTransactionAssetId
    )ERC721(
        "name",
        "symbol"
    ){
       
}
```

See documentation for variables required to deploy to other chain

{% hint style="info" %}
Constructor arguments

*   selfDomain

    The domain ID of the network you deploy

    You can find the ID  [here](../developer-guide/informations.md#domain-id)
*   connext

    The connext handler address of the network you deploy

    You can find the connext addresses  [here](../developer-guide/informations.md#connext-contract-address)
*   dummyTransactionAssetId

    The test ERC20 token address of the network you deploy

    You can find the Test ERC20 address  [here](../developer-guide/informations.md#test-erc20-contract-address)
{% endhint %}



### Example

We provide an example NFT contract like this.\
In this contract, you can specify the token ID that can be minted in each chain.

```
pragma solidity ^0.8.0;

import "@nfthashi/contracts/contracts/native/example/NativeNFT";

contract MyCollectible is NativeNFT {
    constructor(
      uint32 selfDomain,
      address connext,
      address dummyTransactingAssetId,
      uint256 startTokenId,
      uint256 endTokenId,
      string memory name,
      string memory symbol,
      string memory baseTokenURI
  )  {
  }
}
```

{% hint style="info" %}
Constructor arguments

*   selfDomain

    The domain ID of the network you deploy

    You can find the ID  [here](../developer-guide/informations.md#domain-id)
*   connext

    The connext handler address of the network you deploy

    You can find the connext addresses  [here](../developer-guide/informations.md#connext-contract-address)
*   dummyTransactionAssetId

    The test ERC20 token address of the network you deploy

    You can find the Test ERC20 address  [here](../developer-guide/informations.md#test-erc20-contract-address)
*   startTokenId & endTokenId

    Enter how many tokens you want to mint in this chain\
    ex) You want to set token Id 101 \~ 200 to this network, startTokenId is 101 and endTokenId is 200
*   name & symbol & baseTokenURI

    Enter each as you would when creating an ERC721
{% endhint %}



For example, when deploying to rinkeby with token ID 101 \~ 200 sets, the arguments would look like this.

```
pragma solidity ^0.8.0;

import "@nfthashi/contracts/contracts/native/example/NativeNFT";

contract MyCollectible is NativeNFT {
    constructor() NativeNFT(
      1111,
      a0x2307Ed9f152FA9b3DcDfe2385d279D8C2A9DF2b0,
      0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9,
      101,
      200,
      TEST TOKEN NFT,
      TEST,
      www.nfthashi.com/metadata/
  )  {
  }
}
```

_If you're new to smart contract development, head to_ [_Developing Smart Contracts_](https://docs.openzeppelin.com/learn/developing-smart-contracts) _to learn about creating a new project and compiling your contracts. This Openzeppelin Document help your understanding._
