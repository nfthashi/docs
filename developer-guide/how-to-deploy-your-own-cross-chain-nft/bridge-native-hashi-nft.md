# Bridge Native Hashi NFT

If the contract is verified, you can send a transaction from etherscan.

Go to the etherscan page of the NFT contract address you want to bridge,\
Contract => Connect your web3 wallet => Write contract => 11. xSend\
\
xSend is a function that is used to bridge NFTs.\
You can bridge your NFTs by entering these arguments and sending a transaction.

* from : the address of the owner of an NFT
* to : the address you want to send to
* tokenID  the token ID you want to send .
* sendToDomain : the domain ID of the destination chain.  => [DomainID](../informations.md#domain-id)

For example, when sending to Kovan, input like this.

![](<../../.gitbook/assets/image (1).png>)
