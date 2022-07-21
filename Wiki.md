# Block 2 Trace | WIKI


To run a block 2 trace node , you must have the following installed:

    Docker and Docker-compose
 
> **Warning**
> If on MacOS or Windows, please ensure that you allow docker to use upto 6g. The Docker for Mac and Docker Desktop sites have details on how to do this at   the "Resources" heading

    On Windows ensure that the drive that this repo is cloned onto is a "Shared Drive" with Docker Desktop
    On Windows we recommend running all commands from GitBash
    Nodejs or Yarn
    



**Dev Network Setup**

All of our documentation guidelines can be found in [Besu Documentation Site](https://besu.hyperledger.org/en/stable/)

At the beginning the network will be conformed by 4 Validators and one RPC Node and some monitoring tools like:

    -Alethio Lite Explorer to explore blockchain data at the block , transaction and account level 

    -Metric Monitoring via Prometheus and Grafana to give you insigths into how the chain is progressing (Note:This only works with besu other chains    requires other requiremnts to it to work )

    -Optional log monitoring .- This can be execute when the a node that will run receive the params -e

Next we will have the Diagram Architecture as shown below to have a better understanding of the system.

![System Architecture](https://bafkreic4hlcgqtpiixhf33ubado5texsfq6lvytz2stwftdc2sbv776eru.ipfs.nftstorage.link/)

    *Consensus Algorithm*  The besu based Quorum uses IBFT2 consensus mechanism 
    *Private Tx Algorithm* We use [Tessera](https://docs.tessera.consensys.net/en/stable/) so the nodes can send privateTx







