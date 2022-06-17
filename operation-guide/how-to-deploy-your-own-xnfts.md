# How to deploy your own xNFTs

We provide the contract integrated bridge function as SDK for the users who want to create a more advanced NFT utilizing cross-chain. For example, a chain with minted NFTs, a chain with current NFTs, the itinerancy of NFT bridges, and other NFTs whose metadata changes according to these attributes, and so on, will allow for new expressions that have not been possible before!

You can create those NFTs easily by installing SDK and inheriting the contract follow the instructions in the document below.



### Installation

```
$ npm i @nfthashi/contracts
```

The functions and interfaces of each contract are summarized [here.](../developer-guide/sdk-guide.md)

### Usage

Once installed, you can use the contracts in the library by importing them:

When you deploy to Rinkeby, the arguments would be like these.

```
pragma solidity ^0.8.0;

import "@nfthashi/contracts/NativeHashi721.sol";

contract MyNFT is NativeHashi721{
    constructor() NativeHashi721( .  
        1111,                                         /selfDomain ID
        0x2307Ed9f152FA9b3DcDfe2385d279D8C2A9DF2b0,   /Connext handler address
        0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9 .  /dummyTransactionAssetId
    )ERC721(
        "name",
        "symbol"
    ){
       
}
```

See documentation for variables required to deploy to other chains

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

import "@nfthashi/contracts/example/NativeHashi721Example";

contract MyCollectible is NativeHashi721Example {
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

import "@nfthashi/contracts/example/NativeHashi721Example";

contract MyCollectible is NativeHashi721Example {
    constructor() NativeHashi721Example(
      1111,
      a0x2307Ed9f152FA9b3DcDfe2385d279D8C2A9DF2b0,
      0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9,
      101,
      200,
      "TEST TOKEN NFT",
      "TEST",
      "www.nfthashi.com/metadata/"
  )  {
  }
}
```

__

## Deployment

__

Deploy native NFTHashi for Kovan

```
yarn workspace @nfthashi/contracts hardhat native-deploy --network kovan --self-domain 2221 --connext 0x3366A61A701FA84A86448225471Ec53c5c4ad49f --dummy-transacting-asset-id 0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9 --start-token-id 1 --end-token-id 10000
```

Deploy native NFTHashi for Rinkeby

```
yarn workspace @nfthashi/contracts hardhat native-deploy --network rinkeby --self-domain 1111 --connext 0x2307Ed9f152FA9b3DcDfe2385d279D8C2A9DF2b0 --dummy-transacting-asset-id 0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9 --start-token-id 10001 --end-token-id 2000
```

Deploy native NFTHashi for Goerli

```
yarn workspace @nfthashi/contracts hardhat native-deploy --network goerli --self-domain 3331 --connext 0xEC3A723DE47a644b901DC269829bf8718F175EBF --dummy-transacting-asset-id 0x3FFc03F05D1869f493c7dbf913E636C6280e0ff9 --start-token-id 20001 --end-token-id 30000
```

## Register

You should rewrite `self-contract-address` and `opponent-contract-address`

Resister Kovan to Rinkeby

```
yarn workspace contracts hardhat register --network kovan --self-contract-address <YOUR_KOVAN_CONTRACT_ADDRESS> --opponent-domain 1111 --opponent-contract-address <YOUR_RINKEBY_CONTRACT_ADDRESS>
```

Resister Kovan to Goerli

```
yarn workspace contracts hardhat register --network kovan --self-contract-address <YOUR_KOVAN_CONTRACT_ADDRESS> --opponent-domain 3331 --opponent-contract-address <YOUR_GOERLI_CONTRACT_ADDRESS>
```

__

When registering in Rinkeby or Goerli, please also change Self and pponent and enter

## Mint

Mint NFT in Rinkeby

```
yarn workspace contracts hardhat native-mint --network rinkeby --self-contract-address <YOUR_RINKEBY_CONTRACT_ADDRESS> --to <YOUR_WALLET_ADDRESS>
```

Mint NFT in Kovan

```
yarn workspace contracts hardhat native-mint --network kovan --self-contract-address <YOUR_KOVAN_CONTRACT_ADDRESS> --to <YOUR_WALLET_ADDRESS>
```

Mint NFT in Goerli

```
yarn workspace contracts hardhat native-mint --network goerli --self-contract-address <YOUR_GOERLI_CONTRACT_ADDRESS> --to <YOUR_WALLET_ADDRESS>
```



__

_If you're new to smart contract development, head to_ [_Developing Smart Contracts_](https://docs.openzeppelin.com/learn/developing-smart-contracts) _to learn about creating a new project and compiling your contracts. This Openzeppelin document helps your understanding._

__

__
