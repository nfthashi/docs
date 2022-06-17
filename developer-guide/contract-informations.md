# SDK Guide

### INatievHashi721

Required interface of an NativeHashi721 compliant contract.

#### Functions

<details>

<summary>xSend(from, to, tokenId, sendToDomain)</summary>

`xSend(address from, address to, uint256 tokenId, uint32 sendToDomain)`

Send cross-messaging request to Connext \_xCall

Bridge `tokenId`to sendToDomain ’s chain from address `from` to address `to`

</details>



### HashiConnextAdapter

#### Functions

<details>

<summary>constructor (_<em>selfDomain,</em> _<em>connext, _transactingAssetId</em>)</summary>



</details>

<details>

<summary>_bridgeContracts( domainID )</summary>

`_bridgeContracts (uint32 _allowedDomain) ⇒ address _allowedContract`

Return the allowed contract address (messageable address)

</details>

<details>

<summary>setBridgeContract(domain, bridgeContract);</summary>

`setBridgeContract(uint32 domain, address bridgeContract)`

Resister the `domain` to `bridgeContract` mapping

Requirement : onlyOwner

</details>

<details>

<summary>_xcall( destinationDomain, callData)</summary>



</details>



### NativeHashi721

#### Functions

<details>

<summary>xSend(from, to, tokenId, sendToDomain)</summary>

See INativeHashi721.xSend

</details>

<details>

<summary>xReceive(to, tokenId)</summary>

`xReceive(address to, address tokenId)`

Mint `tokenId` to address `to`

</details>

