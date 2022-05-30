# SDK Guide

### IxNFTNativeBridge

Required interface of an xNFTNativeBridge compliant contract.

#### Functions

<details>

<summary>xSend(from, to, tokenId, toDomain)</summary>

`xSend(address from, address to, uint256 tokenId, uint32 toDomain)`

Send cross-messaging request to Connext \_xCall

Bridge `tokenId`to `toDomain` ’s chain from address `from` to address `to`

</details>



### xNFTBridge

#### Functions

<details>

<summary>constructor (_selfDomain, _connext, _dummyTransactingAssetId )</summary>



</details>

<details>

<summary>allowList( domainID )</summary>

`allowlist (uint32 _allowedDomain) ⇒ address _allowedContract`

Return the allowed contract address (messageable address)

</details>

<details>

<summary>register(_allowedDomain, _allowedContract);</summary>

`register(uint32 _allowedDomain, address _allowedContract)`

Resister the `_allowedDomain` to `_allowedContract` mapping

Requirement : onlyOwner

</details>

<details>

<summary>_xcall( destinationDomain, callData)</summary>



</details>



### xNFTNativeBridge

#### Functions

<details>

<summary>xSend(from, to, tokenId, toDomain)</summary>

See IxNFTNativeBridge.xSend

</details>

<details>

<summary>xReceive(to, tokenId)</summary>

`xReceive(address to, address tokenId)`

Mint `tokenId` to address `to`

</details>

