# Setup de un Nodo en la Red de Block2Trace
Block2Trace es una red privada basada en [Hyperledger Besu](https://www.hyperledger.org/use/besu) que implementa el algoritmo del consenso [Clique](https://eips.ethereum.org/EIPS/eip-225).

[Clique](https://eips.ethereum.org/EIPS/eip-225) es un protocolo de consenso de prueba-de-autoridad, cuyo esquema es basado en la idea de que los bloques sólo pueden ser minteados por firmantes confiables. Este consenso fue implementado como respuesta ante los ataques realizados por nodos maliciosos pertenecientes al consenso de prueba-de-trabajo ([Consenso PoW](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)).

La red de Block2Trace posee 3 tipos de nodos:
- **Validadores**: Son los nodos que están a cargo de garantizar el consenso de la red y de la generación de bloques.
- **Bootnodes**: Actúan como intermediarios entre los nodos Regulares y Validadores para así poder contribuir con el descrubrimiento de nodos en la red.
- **Regulares**: Participan replicando la blockchain, aceptando los bloques generados por los validadores y ejecutando las transacciones incluídas en dichos bloques. También están permitidos de inyectar transacciones en la red desde fuentes externas hacia la blockchain. Estos tipos de nodos son usados para la interacción de `Web3.js`, `Ethers` y `Smart Contracts`.

El actual documento es una guía para poder realizar el set up de un nodo de Block2Trace, por medio de la implementación de los siguientes pasos:
1. Instalación y configuración

### :bulb: Revisa la documentación de [Web3.js](https://web3js.readthedocs.io/en/v1.7.4/), [Ethers](https://docs.ethers.io/v5/)!

## 1) Instalación
El siguiente proceso explica la instalación de un nodo regular:
  1) Clone o descargue este repositorio en la máquina que desee instalar y operar el nodo de Block2Trace, luego ingrese en el directorio clonado.
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
   2) Ejecute el siguiente comando:
     <br/>
     <br/>
     - ```
     docker run nodeName
     ```
     <br/>
     <br/>
     Esto va a ejecutar el proceso en el "background". Puede revisar las actividades de los servicios en la siguiente lista de endpoints:
     <br/>
     <br/>
     - **JSON-RPC HTTP service endpoint**: http://localhost:8545
     <br/>
     <br/>
     - **JSON-RPC WebSocket service endpoint**: ws://localhost:8545
     <br/>
     <br/>
     - **Web block explorer address**: http://localhost:25000/
     <br/>
     <br/>
     - **Blockscout address**: http://localhost:26000/
     <br/>
     <br/>
     - **Prometheus address**: http://localhost:9090/graph
     <br/>
     <br/>
     -**Grafana address**: http://localhost:3000/d/XE4V0WGZz/nesu-overview?orgId=1&refresh=10s&from=now-30m&to=now&var-system=All
     <br/>
     <br/>
    3) Listo! 🎊 🎉 🎈


### :bulb: Una Guía Rápida para [docker-compose](https://docs.docker.com/compose/)
