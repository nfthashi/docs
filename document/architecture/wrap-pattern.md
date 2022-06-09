# Wrap Pattern

### Wrap Pattern

Wrap pattern support any NFTs already created. A simple ERC721 contract is deployed on the bridged chain based on the information of the original NFT existing in Chain A (Origin Chain) and minted to the address that caused the Tx. In case of unwrapping from Chain B to Chain A, a wrapped NFT on Chain B will be burned, and an NFT deposited in contract on Chain A will be transferred to the owner on Chain B on Chain A.

Let me describe along with the user flow.



#### Case of bridge from Chain A to Chain B：Wrap

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.44.36.png>)

* Deposit an NFT to NFT Hashi handler contract on Chain A (Origin Chain)
* The handler contract sends the information of NFT or chains to Chain B using xCall supported by Connext. (more info about xCall ⇒ [xapp-starter](https://github.com/connext/xapp-starter)
* The Handler Contract of Chain B receives the xCall from Chain A
* Compute the contract address from the information of these using Create2.
* If the computed address has not been deployed, the wrapped NFT contract is deployed to the computed contract address and minted. After the second time, the NFT is minted from a contract that has already been deployed.



#### Case of bridge from Chain B to Chain A: Dewrap

![](<../../.gitbook/assets/Screen Shot 2022-05-25 at 14.46.09.png>)

* The bridge contract burns the wrapped NFT minted on Chain B
* Refer the mapping of Chain A address and Chain B address
* Send NFT information to Chain A using xCall
* The Handler Contract of Chain B receive the xCall from Chain A
* An NFT deposited in contract with Chain A will be transferred to the address of an owner at Chain B
