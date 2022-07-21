# Block2Trace Node Setup for Block2Trace Network
Block2Trace Network is a [Hyperledger Besu](https://www.hyperledger.org/use/besu) private network that uses the [Clique](https://eips.ethereum.org/EIPS/eip-225) consensus algorithm.

[Clique](https://eips.ethereum.org/EIPS/eip-225) is a proof-of-authority consensus protocol, which scheme is based on the idea that blocks may only be minted by trusted signers. This consensus was implemented in response to attaks the made by malicious nodes belonging to the proof-of-work networks ([PoW consensus](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)).

Block2Trace Network has 3 types of nodes:
- **Validators**: Nodes that are in charge of guaranteeing the consensus of the network and the generation of blocks. 
- **Bootnodes**: They act like intermediaries between Regular and Validator nodes in order to contribute to the node discovery of the network.
- **Regular**: They participate by replicating the blockchain, accepting the blocks generated by the validators and executing the transactions included in them. They are also allowed to inject transactions into the network from sources external to the blockchain. These kind of nodes are used for the interaction from `Web3.js`, `EthersJS` and `Smart Contracts`. Usually these interactions are related with the development of blockchain-related applications.

The following doc will guide you on how to set up a Block2Trace node, by following the next steps:
1. Installation & configuration
2. Getting permissions

If a node wants to be removed, you can etc.

## 1) Installation
The following process explains the installation for a regular node:
  1) Clone or download this repository to the machine where you want to install and operate the Block2Trace node, then enter into the cloned directory.
    <br/>
    <br/>
    - ```
    git clone https://github.com/Block2Trace/Block2Trace.git
    ```
    <br/>
    <br/>
    - ```
    cd Block2Trace
    ```
    <br/>
    <br/>
  3) Execute the following command:
     <br/>
     <br/>
     - ```
     docker run nodeName
     ```
     <br/>
     <br/>
  5) You're done! 🎊 🎉 🎈

###  :bulb: A Quick Guide for [docker-compose](https://docs.docker.com/compose/)

## 2) Permissioning New Node
