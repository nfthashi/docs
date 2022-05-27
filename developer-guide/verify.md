# Verify

## Set Environment Variables

\
Set private_key and etherscan\__api\_key to environment variable.

```
export PRIVATE_KEY = <YOUR_PRIVATE_KEY>
export ETHERSCAN_API_KEY = <YOUR_ETHERSCAN_API_KEY>
```

If you don't have your etherscan_api_key, please check this documentation and sign up to get\
[https://etherscan.io/apis](https://etherscan.io/apis)\


## Command

To verify the contract, you need to input some arguments. Arrange and use the <> part.

```
 yarn hardhat verify --network <NETWORK_NAME> <address(YOUR_CONTRACT)> <SELF_DOMAIN> <address(CONNEXT)> <address(TEST_ERC20)> <START_TOKENID> <END_TOKEN_ID> <CONTRACT_NAME> <CONTRACT_SYMBOL> <BASE_TOKEN_URI>
```

Domain, address(Connext), address(Test ERC20) are written in [Informations](informations.md)\
\
\
**Example**

For ex, you want to verify `0x0Ee964Acc426237998e5015C176D06744f64aE59` contract to kovan, the command to verify etherscan would be like this.

```
yarn hardhat verify --network kovan 0x0Ee964Acc426237998e5015C176D06744f64aE59 2221 0x3366A61A701FA84A86448225471Ec53c5c4ad49f 0x3ffc03f05d1869f493c7dbf913e636c6280e0ff9 222 333 TEST TEST http:localhost:3000/
```

When verification is completed, such messages will be appeared.

```
Successfully verified contract NativeNFT on Etherscan.
https://kovan.etherscan.io/address/0x0Ee964Acc426237998e5015C176D06744f64aE59#code
```

