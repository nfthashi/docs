# How to check NFT bridge status

* Copy the transaction hash on the origin chain
* Use this code in subQuery of the origin chain to get “Transaction ID”
  * subgraph URL
    * Kovan [https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-kovan](https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-kovan)
    * Rinkeby [https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-rinkeby](https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-rinkeby)

```
{
 originTransfers(
   where: {
     transactionHash: "<your_transaction_hash>"
   }
 ) {
   transferId
 }
}
```

*   Use this code in subQuery of the destination chain to get the transaction hash

    \*It takes about an hour to send message from Chain A to Chain B

```
{
destinationTransfers(
  where: {
    transferId: "<your_transfer_id>"
  }
) {
  executedTransactionHash
}
}
```

For more information about this section, this documentation will help you

* [https://docs.connext.network/Developers/xcall-status](https://docs.connext.network/Developers/xcall-status)
