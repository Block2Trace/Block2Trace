# Block2Trace | WIKI
Para ejecutar un nodo de Block2Trace, debe tener instalado lo siguiente:

  Docker and docker-compose
  
> **Warning**
> Si se encuentra en MacOS o Windows, por favor verifique si docker tiene permitido utilizar hasta 6g. Los sitios [Docker for Mac](https://docs.docker.com/desktop/mac/) y el [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) poseen los detalles de cómo hacer esto en la sección de "Resources".

> **Note**
> En Windows, asegùrese de que el drive en el que se clone este repositorio sea un "Drive Compartido" con Docker Desktop. Se recomienda ejecutar todos los comandos de `GitBash`, `Nodejs` o `Yarn`.

### Dev Network Setup
La guía de toda nuestra documentación puede ser hallada en [Sitio de Documentación de Besu](https://besu.hyperledger.org/en/stable/).

Inicialmente, la red va a estar conformada por 4 nodos validadores y un nodo RPC, junto a otras herramientas de monitoreo como:
<br/>
- **Alethio Lite Explorer**: para explorar la data de la blockchain a nivel de bloque, transacción y cuenta
- **Metric Monitoring via Prometheus y Grafana**: brinda insights de cómo progresa la cadena de bloques. (Nota: Esto sólo funciona con besu, con otras cadenas se necesitan otros requerimientos para su funcionamiento)
- **Optional log monitoring**: esto se puede ejecutar cuando un nodo que va a ejecutarse recibe los parámetros -e.

## Diagrama de Arquitectura
![System Architecture](https://bafkreic4hlcgqtpiixhf33ubado5texsfq6lvytz2stwftdc2sbv776eru.ipfs.nftstorage.link/)

###### Consensus Algorithm: The besu based Quorum uses IBFT2 consensus mechanism 
###### Private Tx Algorithm: We use [Tessera](https://docs.tessera.consensys.net/en/stable/) so the nodes can send privateTx
