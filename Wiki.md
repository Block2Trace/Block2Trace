# Block 2 Trace | WIKI


To run a block 2 trace node , you must have the following installed:

    Docker and Docker-compose
 
> **Warning**
> If on MacOS or Windows, please ensure that you allow docker to use upto 6g. The [Docker for Mac](https://docs.docker.com/desktop/mac/) and [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) sites have details on how to do this at the "Resources" heading

> **Note**
> On Windows ensure that the drive that this repo is cloned onto is a "Shared Drive" with Docker Desktop. On Windows we recommend running all commands from `GitBash`, `Nodejs` or `Yarn`.
    



### Dev Network Setup**

All of our documentation guidelines can be found in [Besu Documentation Site](https://besu.hyperledger.org/en/stable/)

At the beginning the network will be conformed by 4 Validators and one RPC Node and some monitoring tools like:

- **Alethio Lite Explorer**: to explore blockchain data at the block , transaction and account level 

- **Metric Monitoring via Prometheus and Grafana**: to give you insigths into how the chain is progressing (Note:This only works with besu other chains requires other requiremnts to it to work )

- **Optional log monitoring**: This can be execute when the a node that will run receive the params -e.

## Architecture Diagram

Next we will have the Diagram Architecture as shown below to have a better understanding of the system.

![System Architecture](https://bafkreic4hlcgqtpiixhf33ubado5texsfq6lvytz2stwftdc2sbv776eru.ipfs.nftstorage.link/)

###### Consensus Algorithm: The besu based Quorum uses IBFT2 consensus mechanism 
###### Private Tx Algorithm: We use [Tessera](https://docs.tessera.consensys.net/en/stable/) so the nodes can send privateTx

# POA Network 

The network for sign transactions that will be added to the block uses an Eth Signer Proxy to make this work.

For monitoring how the chain work we can use the Alethio block Explorer  , we can use Prometheus to query blockchain data this paired with grafana  is a great bomb of data to understand how the networks works.

**The uses cases for this monitoring tools:**

- You are a Dapp Developer looking for a robust simple network for deploying huge projects and need all the metric to build a great front-end for the end user to have all the information to accomplish the full potential of blockchain we can see that the mayority of this can’t be accomplish in other networks because the price of the tools and gass issues that are native of the chain
- Want to be part of the blockchain but in a small network.

# POA Network & Privacy 

The nodes in Block2Trace are each paired with Tessera for its Private Transaction Manager
Use cases: 
    • You are a user looking to execute private transactions at least one other party 
    • You are looking to create a private Ethereum network with private transactions between two or more parties. 
Once the network is up and running you can make public transactions on the chain and interact with the smart contract at its deployed address, and you can also make private transaction between members and verify that other nodes do not see it. 

**For the public transaction:**
```
    cd smart_contracts
    npm install
    node scripts/public_tx.js
    This is a brief look of the public transaction 
    node scripts/public_tx.js 
    {
      address: '0x36781cB22798149d47c55A228f186F583fA9F64b',
      privateKey: '0x6ee9f728b2e4c092243427215ecd12e53b9c0e388388dc899b1438c487c02b61',
      signTransaction: [Function: signTransaction],
      sign: [Function: sign],
      encrypt: [Function: encrypt]
    }
    Creating transaction...
    Signing transaction...
    Sending transaction...
    tx transactionHash: 0xaf86a44b2a477fbc4a7c9f71eace0753ac1ffc4c446aa779dbb8682bf765e8b9
    tx contractAddress: 0xE12f1232aE87862f919efb7Df27DC819F0240F07
    Contract deployed at address: 0xE12f1232aE87862f919efb7Df27DC819F0240F07
    Use the smart contracts 'get' function to read the contract's constructor initialized value .. 
    Obtained value at deployed contract is: 47
    Use the smart contracts 'set' function to update that value to 123 .. 
    Verify the updated value that was set .. 
    Obtained value at deployed contract is: 123
```

**For the private transaction:**
```
    cd smart_contracts
    npm install
    node scripts/private_tx.js
    For this example  the deploys of the contract sends an arbitrary value (47) from Member1 to Member3. Once done, it queries all three members (tessera) to check the value at an address, and you should observe that only Member1 & Member3 have this information as they were involved in the transaction and that Member2 responds with a 0x to indicate it is unaware of the transaction.
    node scripts/private_tx.js
    Creating contract...
    Getting contractAddress from txHash:  0xc1b57f6a7773fe887afb141a09a573d19cb0fdbb15e0f2b9ed0dfead6f5b5dbf
    Waiting for transaction to be mined ...
    Address of transaction: 0x8220ca987f7bb7f99815d0ef64e1d8a072a2c167
    Use the smart contracts 'get' function to read the contract's constructor initialized value .. 
    Waiting for transaction to be mined ...
    Member1 value from deployed contract is: 0x000000000000000000000000000000000000000000000000000000000000002f
    Use the smart contracts 'set' function to update that value to 123 .. - from member1 to member3 
    Transaction hash: 0x387c6627fe87e235b0f2bbbe1b2003a11b54afc737dca8da4990d3de3197ac5f
    Waiting for transaction to be mined ...
    Verify the private transaction is private by reading the value from all three members .. 
    Waiting for transaction to be mined ...
    Member1 value from deployed contract is: 0x000000000000000000000000000000000000000000000000000000000000007b
    Waiting for transaction to be mined ...
    Member2 value from deployed contract is: 0x
    Waiting for transaction to be mined ...
    Member3 value from deployed contract is: 0x000000000000000000000000000000000000000000000000000000000000007b
    Further documentation for this example and a video tutorial is also available.
    We will provide this scripts for further usage.
    There is an additional erc20 token example that you can also test with: executing node example/erc20.js deploys a HumanStandardToken contract and transfers 1 token to Node2.
    This can be verified from the data field of the logs which is 1.
```




