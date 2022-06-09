# How to check NFT bridge status

### Get transfer ID

* Copy the transaction hash on the origin chain
* Use this code in the subQuery of the original chain to get “Transaction ID”
  * subgraph URL
    *   Kovan

        &#x20;[https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-kovan](https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-kovan)
    *   Rinkeby

        &#x20;[https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-rinkeby](https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-rinkeby)
    *   Goerli

        [https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-goerli](https://thegraph.com/hosted-service/subgraph/connext/nxtp-amarok-runtime-v0-rinkeby)

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

For more information about this section, this documentation will help you

* [https://docs.connext.network/Developers/xcall-status](https://docs.connext.network/Developers/xcall-status)



### Check transfer status

Go to connextscan page and search transferId you got before\
[https://testnet.amarok.connextscan.io/](https://testnet.amarok.connextscan.io/tx/0xcd05fea9a1d781cf759748b415d9dc85cb61c1ec33f40c1cc3e6cdc332c671f9?src=search)



If everything goes well and the token was transferred, a screeen like this will appear.\
The transaction hash in the Execute confirms that the token is minted at the bridge destination.

Immediatery after bridge your NFT, connextscan page will return 404 Error to your browser.

![](<../.gitbook/assets/Screen Shot 2022-06-01 at 20.21.20.png>)
