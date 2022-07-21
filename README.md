### Block2Trace Node Setup for Block2Trace Network
Block2Trace Network is a [Hyperledger Besu](https://www.hyperledger.org/use/besu) private network that uses the [Clique](https://eips.ethereum.org/EIPS/eip-225) consensus algorithm.

[Clique](https://eips.ethereum.org/EIPS/eip-225) is a proof-of-authority consensus protocol, which scheme is based on the idea that blocks may only be minted by trusted signers. This consensus was implemented in response to attaks the made by malicious nodes belonging to the proof-of-work networks ([PoW consensus](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)).

Block2Trace Network has 3 types of nodes:
- **Validators**: Nodes that are in charge of guaranteeing the consensus of the network and the generation of blocks. They do this via the [Clique](https://eips.ethereum.org/EIPS/eip-225) consensus.
- **Bootnodes**: Authorization or enabling of the Permitting Nodes to the Regular Nodes so that, using the gas limit granted, they propose (initiate), carry out (write), or consult (read) transactions. They act like proxy between Regular and Validator nodes.
- **Regular**: They participate and replicating the blockchain, accepting the blocks generated by the valdators and executing the transactions included in them. They are also allowed to inject transactionsinto the network from sources external to the blockchain. These kind of nodes are use for the interaction from Web3.js, EthersJS and Smart Contracts.

The following doc will guide you on how to set up a Block2Trace node, by following the next steps:
1. Installation & configuration
2. Getting permissions

If a node wants to be removed, you can etc.

## 1) Installation
The following process explains the installation for a regular node:
  1) Clone or download this repository to the machine where you want to install and operate the Block2Trace node, then enter into the cloned directory.
    -```
    git clone https://github.com/Block2Trace/Block2Trace.git
    ```
  3) Edit the .env file and modify the lines with:
  4) Edit the docker-compose.yml and make your own changes
  5) In the root directory of the repository (where the file docker-compose.yml exists) run:
  The command runs the service in the background, and you can check its activity by running:
  5) You're done!

A Quick Guide for [docker compose](https://docs.docker.com/compose/)
<!--
**Block2Trace/Block2Trace** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
