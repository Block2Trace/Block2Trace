# Plataforma técnica básica de Block2Trace
## Requerimientos y desafíos para una red blockchain de un país

<!-- TOC -->

- [Plataforma técnica básica de Block2Trace](#plataforma-técnica-básica-de-block2trace)
    - [Requerimientos y desafíos para una red blockchain de un país](#requerimientos-y-desafíos-para-una-red-blockchain-de-un-país)
1. [Objetivo](#1-objetivo)
2. [Introducción](#2-introducción)
3. [Características generales de las principales tecnologías blockchain](#3-características-generales-de-las-principales-tecnologías-blockchain)
4. [Las redes blockchain públicas sin permisos](#4-las-redes-blockchain-públicas-sin-permisos)
    - 4.1 [El problema de la escalabilidad de las cadenas de bloques con permiso público](#41-el-problema-de-la-escalabilidad-de-las-cadenas-de-bloques-con-permiso-público)
    - 4.2 [El problema de los Costos de Transacción Altos y Volátiles](#42-el-problema-de-los-costos-de-transacción-altos-y-volátiles)
    - 4.3 [El problema de la Privacidad](#43-el-problema-de-la-privacidad)
        - 4.3.1 [Confidencialidad de Datos](#431-confidencialidad-de-datos)
        - 4.3.2 [Privacidad de Actividades Transaccionales](#432-privacidad-de-actividades-transaccionales)
5. [LAS REDES BLOCKCHAIN DEL CONSORCIO PRIVADO](#5-las-redes-blockchain-del-consorcio-privado)
    - 5.1 [Una "compensación de confianza" diferente](#51-una-"compensación-de-confianza"-diferente)
    - 5.2 [Un modelo de incentivación diferente para los nodos operativos](#52-un-modelo-de-incentivación-diferente-para-los-nodos-operativos)
    - 5.3 [Un modelo diferente para la ejecución de transacciones](#53-un-modelo-diferente-para-la-ejecución-de-transacciones)
6. [BLOCK2TRACE UNA BLOCKCHAIN CON PERMISO PÚBLICO](#6-block2trace-una-blockchain-con-permiso-público)
7. [REQUERIMIENTOS GENERALES SOBRE EL SOFTWARE](#7-requerimientos-generales-sobre-el-software)
    - 7.1 [Basado en OpenSource de amplia aceptación en el mercado](#71-basado-en-opensource-de-amplia-aceptación-en-el-mercado)
    - 7.2 [El ecosistema de usuarios del software debe ser lo más amplio posible](#72-el-ecosistema-de-usuarios-del-software-debe-ser-lo-más-amplio-posible)
    - 7.3 [Block2Trace debe basarse en plataformas multisectoriales y de uso general](#73-block2trace-debe-basarse-en-plataformas-multisectoriales-y-de-uso-general)
    - 7.4 [Block2Trace permitirá y facilitará el cumplimiento normativo por parte de los miembros, en particular](#74-block2trace-permitirá-y-facilitará-el-cumplimiento-normativo-por-parte-de-los-miembros,-en-particular)
8. [ARQUITECTURA DE REFERENCIA DE UNA BLOCKCHAIN](#8-arquitectura-de-referencia-de-una-blockchain)
    - 8.1 [Capa de infraestructura](#81-capa-de-infraestructura)
        - 8.1.1 [Almacenamiento de Datos](#811-almacenamiento-de-datos)
        - 8.1.2 [Entorno de tiempo de ejecución (cómputo)](#812-entorno-de-tiempo-de-ejecución-(cómputo))
        - 8.1.3 [Redes de comunicación](#813-redes-de-comunicación)
    - 8.2 [Capa de plataforma DLT](#82-capa-de-plataforma-dlt)
        - 8.2.1 [Tiempo de Ejecución Seguro](#821-tiempo-de-ejecución-seguro)
        - 8.2.2 [Contratos Inteligentes](#822-contratos-inteligentes)
        - 8.2.3 [Ledger](#823-ledger)
        - 8.2.4 [Gestión de Estados](#824-gestión-de-estados)
        - 8.2.5 [Sistema de Transacciones](#825-sistema-de-transacciones)
        - 8.2.6 [Servicios de Membresía](#826-servicios-de-membresía)
        - 8.2.7 [Mecanismo de Consenso](#827-mecanismo-de-consenso)
            - 8.2.7.1 [Nodos de confianza y validación en IBFT](#8271-nodos-de-confianza-y-validación-en-ibft)
            - 8.2.7.2 [Selección de nodos validadores](#8272-selección-de-nodos-validadores)
            - 8.2.7.3 [Número de nodos validadores](#8273-número-de-nodos-validadores)
        - 8.2.8 [Distribución de Eventos](#828-distribución-de-eventos)
        - 8.2.9 [Servicios Crypto](#829-servicios-crypto)
        - 8.2.10 [Comunicación entre nodos segura](#8210-comunicación-entre-nodos-segura)
    - 8.3 [Capa API](#83-capa-api)
        - 8.3.1 [Interfaces Externas](#831-interfaces-externas)
        - 8.3.2 [API de Usuario](#832-api-de-usuario)
        - 8.3.3 [API de Administrador](#833-api-de-administrador)
    - 8.4 [Capa de usuario](#84-capa-de-usuario)
        - 8.4.1 [Aplicaciones de usuario](#841-aplicaciones-de-usuario)
        - 8.4.2 [Aplicaciones de administración](#842-aplicaciones-de-administración)
    - 8.5 [Capa de Sistemas No-DLT](#85-capa-de-sistemas-no-dlt)
        - 8.5.1 [Oráculo DLT](#851-oráculo-dlt)
        - 8.5.2 [Aplicaciones No-DLT](#852-aplicaciones-no-dlt)
        - 8.5.3 [Datos Off Ledger](#853-datos-off-ledger)
    - 8.6 [Funciones de Capa-Cruzada](#86-funciones-de-capa-cruzada)
        - 8.6.1 [Desarrollo](#861-desarrollo)
            - 8.6.1.1 [IDE (Entorno de Desarrollo Integrado)](#8611-ide-(entorno-de-desarrollo-integrado))
            - 8.6.1.2 [Gestión de Compilación](#8612-gestión-de-compilación)
            - 8.6.1.3 [Gestión de pruebas](#8613-gestión-de-pruebas)
        - 8.6.2 [Gestión y Operaciones](#862-gestión-y-operaciones)
            - 8.6.2.1 [Directorio de Servicios](#8621-directorio-de-servicios)
            - 8.6.2.2 [Gestión de Incidentes](#8622-gestión-de-incidentes)
            - 8.6.2.3 [Gestión de Entrega](#8623-gestión-de-entrega)
            - 8.6.2.4 [Gestión de Nodos](#8624-gestión-de-nodos)
            - 8.6.2.5 [Gestión de Ledger](#8625-gestión-de-ledger)
            - 8.6.2.6 [Gestión de Sistemas DLT](#8626-gestión-de-sistemas-dlt)
            - 8.6.2.7 [Monitoreo](#8627-monitoreo)
            - 8.6.2.8 [Gestión de Actualización y Versionamiento](#8628-update-and-version-management)
        - 8.6.3 [Capacidades de Seguridad](#863-security-capabilities)
            - 8.6.3.1 [Gestión de Autenticación e Identidad](#8631-gestión-de-autenticación-e-identidad)
            - 8.6.3.2 [Gestión de políticas de seguridad](#8632-gestión-de-políticas-de-seguridad)
            - 8.6.3.3 [Gestión de Acceso](#8633-gestión-de-acceso)
            - 8.6.3.4 [Protección PII](#8634-protección-pii)
        - 8.6.4 [Gobernanza y Cumplimiento](#864-governanza-y-cumplimiento)
            - 8.6.4.1 [Soporte de Supervisión](#8641-soporte-de-supervisión)
            - 8.6.4.2 [Soporte de Auditoría](#8642-soporte-de-auditoría)
            - 8.6.4.3 [Controles de Gobernanza](#8643-controles-de-governanza)
            - 8.6.4.4 [Gestión de Políticas](#8644-gestión-de-políticas)

<!-- /TOC -->

# 1. Objetivo
This document describes the requirements and challenges for a country blockchain network like Alastria. While the document tries to be as technology-agnostic as possible, there are subjects where we have to focus on a given technology, and when this is the case, we discuss the initial implementation using Quorum. However, the intention is to include specific analyses for other technologies like Hyperledger.  This document is live and continuously evolving, describing the current situation of the technology with respect to the requirements and the challenges that have to be solved.

# 2. Introducción

Alastria is a Spanish nonprofit association with the objective to create the first multi-industry national blockchain network, to support transactions with full legal validity, and with appropriate levels of privacy.

We are currently more than 250 companies and institutions from different sectors like banking, telco, energy, insurance, law firms, technology and services companies, research institutions, universities, etc.. The association is growing, because it is inclusive and open to anybody who would like to collaborate and participate in the initiative.

The associates of Alastria are collaborating with each other in the definition, deployment, operation and maintenance of the infrastructure, but will compete with each other in the specific use cases built on top of the network.

Being a country-wide blockchain network, Alastria is neither a public-permissionless network nor a private consortium. Alastria shares some of the properties of both types of networks, but it has some requirements of its own. This document is structured as follows:
* The first two sections describe the general characteristics of Public-Permissionless and Consortium blockchains and the problems that they present for a network like Alastria
* Then we describe the specific requirements of Alastria, using as a scheme and guiding theme a general Reference Architecture of blockchains systems

# 3. Caracter

Distributed fault tolerant protocols have been deployed traditionally at relatively small scale, and typically in a single administrative domain (that is, inside a single legal company) where adversarial attacks can be minimized and so they are not a primary concern.

[Bitcoin](https://bitcoin.org/bitcoin.pdf) was the first practical system to solve the problem of fault tolerant distributed computing in a completely public and anonymous environment where anonymous malicious adversaries could behave in a [Byzantine](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance) way to try to make the network malfunction.

Possibly the major invention of the Bitcoin system was to design a consensus mechanism with an embedded digital currency, where agreement on the order of transactions is negotiated via an economically incentivized cryptographic random lottery based on partial hash collisions. This novel consensus algorithm was called Proof-of-Work (PoW), reflecting the idea that in order to win the lottery, the nodes had to use a lot of computational resources to solve the cryptographic puzzle used for the lottery.

Apart from enabling the consensus on the order of transactions, the PoW mechanism provides two additional benefits: on one hand it protects the system from Sybil attacks (especially difficult to avoid in public-permissionless networks), and on the other it creates a very good incentivisation mechanism for promoting anonymous participants to dedicate expensive computing resources to execute the consensus algorithm required for the operation of the network and ensuring safety.

The [Bitcoin](https://bitcoin.org/bitcoin.pdf) and [Ethereum](https://www.ethereum.org/) systems are very robust and they operate successfully in a highly adversarial environment, where highly-motivated and malicious attacks are commonplace, and does so in spite of the anonymity of the entities operating the nodes in a fully decentralized way. This is the reason why the system is many times referred to as the “Trustless machine”.

> A brief note on terminology: we refer to these types of networks as "Public-Permissionless" to stress the fact that the participants do not need to request permission to anybody in order to participate in the network. It is very common in the literature to drop the "Permissionless" word and just use "Public" to mean both accessible to anybody and without the need to request permission.
>
> However, in other contexts, the word "Public" does not necessarily imply the anonymous access to the services provided in a public manner. For example, in order to access to the public health services of a country, their citizens normally have to identify themselves to the entity providing the service. In those other contexts there are many examples of both Public-anonymous and Public-identified provision of public services.
>
> Indeed, we will see that Alastria has the objective of being a Public-Permissioned network, in the sense that is is open to all entities in Spain, but it is permissioned so the entities have to be identified.
Soon, the underlying technology powering these systems started to find applicability in other environments where the requirements for decentralization were not so high, even though it was required a high level of collaboration among peers (typically enterprises), higher than what was possible with the current centralized technologies. A set of distributed systems started to appear with some characteristics that were not possible before, with numerous fields of application and with enormous potential for innovation.

A class of these systems is what is known as Private Consortiums Blockchains, because they have the objective to improve efficiency in the creation of consortiums or groups of companies and entities, without the existence of centra entities which operate a centralized database or transactional system, acting as the central point to which all other entities have to connect. In this sense, we can say that private consortium blockchains allow the implementation of the P2P paradigm among companies, instead of among individuals, as it was the original objective of Bitcoin.

Two of the most widely used technologies for private consortiums are Quorum and Hyperledger Fabric (or simply Fabric).
In order to understand the pros and cons of the different technologies, it is first convenien to analyze some of the characteristics of blockchain systems, public and private, and how Ethereum, Quorum and Fabric approach each of those characteristics.

In the following sections, we analyze the different tecnologies according to these characteristics:

* Transaction execution model
* Scalability
* Immutability
* Privacy
* Safety

# 4. Las redes blockchain públicas sin permisos

Distributed fault tolerant protocols have been deployed traditionally at relatively small scale, and typically in a single administrative domain (that is, inside a single legal company) where adversarial attacks can be minimized and so they are not a primary concern.

[Bitcoin](https://bitcoin.org/bitcoin.pdf) was the first practical system to solve the problem of fault tolerant distributed computing in a completely public and anonymous environment where anonymous malicious adversaries could behave in a [Byzantine](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance) way to try to make the network malfunction.

Possibly the major invention of the Bitcoin system was to design a consensus mechanism with an embedded digital currency, where agreement on the order of transactions is negotiated via an economically incentivized cryptographic random lottery based on partial hash collisions. This novel consensus algorithm was called Proof-of-Work (PoW), reflecting the idea that in order to win the lottery, the nodes had to use a lot of computational resources to solve the cryptographic puzzle used for the lottery.

Apart from enabling the consensus on the order of transactions, the PoW mechanism provides two additional benefits: on one hand it protects the system from Sybil attacks (especially difficult to avoid in public-permissionless networks), and on the other it creates a very good incentivisation mechanism for promoting anonymous participants to dedicate expensive computing resources to execute the consensus algorithm required for the operation of the network and ensuring safety.

The [Bitcoin](https://bitcoin.org/bitcoin.pdf) and [Ethereum](https://www.ethereum.org/) systems are very robust and they operate successfully in a highly adversarial environment, where highly-motivated and malicious attacks are commonplace, and does so in spite of the anonymity of the entities operating the nodes in a fully decentralized way. This is the reason why the system is many times referred to as the “Trustless machine”.

A brief note on terminology: we refer to these types of networks as "Public-Permissionless" to stress the fact that the participants do not need to request permission to anybody in order to participate in the network. It is very common in the literature to drop the "Permissionless" word and just use "Public" to mean both accessible to anybody and without the need to request permission.

However, in other contexts, the word "Public" does not necessarily imply the anonymous access to the services provided in a public manner. For example, in order to access to the public health services of a country, their citizens normally have to identify themselves to the entity providing the service. In those other contexts there are many examples of both Public-anonymous and Public-identified provision of public services.

Indeed, we will see that Alastria has the objective of being a Public-Permissioned network, in the sense that is is open to all entities in Spain, but it is permissioned so the entities have to be identified.

## 4.1. El problema de la escalabilidad de las cadenas de bloques con permiso público
However, achieving this level of robustness in such a hostile environment can not be made without some compromises. Those compromises are better illustrated using the words of Vitalik Buterin describing the **“Blockchain trilemma”**. The trilemma claims that blockchain systems can only at most have two of the following three properties:
* **Decentralization**, defined as the system being able to run in a scenario where each participant only has access to O(c) resources, where c refers to the size of computational resources available to each node (ie. a regular laptop or small VPS).
* **Scalability**, defined as being able to process O(n) > O(c) transactions, where n refers to the size of the ecosystem in some abstract sense.
* **Security (or Safety)**, defined as being secure against attackers with up to O(n) resources

For the reasons described above, Public-Permissionless blockchains have chosen Decentralization and Security over Scalability.

In general, we assume that in practice all useful implementations of blockchain systems will always want to stress Safety, so we are in reality faced with a dilemma between Decentralization and Scalability, which we call the “Trust continuum” as shown in Figure 1.

But it happens that these properties are not binary all-or-nothing, especially if we add permissioning into the picture, as it will be discussed below.

As Figure 1 describes, the prevailing public-permissionless blockchain networks currently in production like Bitcoin or Ethereum have the very desirable property of being “Trustless”, but due mainly to the characteristics of the consensus algorithms used to achieve that property, they suffer from very well documented scalability problems. There are a lot of efforts being made to solve or alleviate the scalability problem, but as of today, the problem still exists and permissioned networks will always have several orders of magnitude better performance.

***

![Trust Continuum](/assets/Trust%20continuum_%20trustless%20vs%20centralized.jpg)
<p align="center"><b>Fig1. - The Trust Continuum.</b></p>

***

## 4.2. El problema de los Costos de Transacción Altos y Volátiles
As we mentioned before, we expect that all practical implementations of blockchains would not compromise on Security.

In such a highly adversarial environment as a public anonymous fully decentralized network, there should be crypto-economic incentives for the miner nodes to perform their duties and ensure the security of the network. As Vitalik Buterin says in ["On Inflation, Transaction Fees and Cryptocurrency Monetary Policy"](https://blog.ethereum.org/2016/07/27/inflation-transaction-fees-cryptocurrency-monetary-policy/):
> The primary expense that must be paid by a blockchain is that of security. The blockchain must pay miners or validators to economically participate in its consensus protocol, whether proof of work or proof of stake, and this inevitably incurs some cost. There are two ways to pay for this cost: inflation and transaction fees. Currently, Bitcoin and Ethereum, the two leading proof-of-work blockchains, both use high levels of inflation to pay for security.
As described in Figure 1, those crypto-economic incentives for the miner nodes cause that the transaction costs for users of the network are very high and very volatile. While this is not a problem for some uses cases (specially ones requiring very low transaction volumes), high and unpredictable transaction costs constitute a critical limitation for a network like Alastria where we expect the provision of basic services and a very high number of transactions, many of them with low added-value for the originator but still required for the implementation of the commercial transactions.

Expected improvements to the current public-permissionless blockchain systems may alleviate somewhat this problem, but they will not solve the fundamental problem of securing the network in conditions of anonymity.

## 4.3. El problema de la Privacidad
By default, in public blockchains like Bitcoin or Ethereum, transactions are executed by all nodes in the network, transactions are globally published and state data is not encrypted in most applications, so all participants have access to all data stored in the ledger without any restriction.

In many cases, the only privacy mechanism is the pseudonymity nature of account addresses involved in the transactions, which is a poor method to provide real privacy.

There are many efforts to incorporate natively in the blockchain privacy-preserving technologies, with the promise that they will allow users to benefit from the security of a blockchain, using a decentralized network to process the transactions, but “encrypting” the data in such a way that even though everything is being computed in plain sight, the underlying “meaning” of the information is completely obfuscated.

This is what Vitalik Buterin calls the “holy grail” of blockchain privacy technology, and the technologies  are promising but currently they are either too cumbersome or too slow (or both) for widespread and immediate adoption by the majority of developers.

Discussing in detail the “holy grail” of privacy-enhancing technologies is out of scope for this document (but is the subject of a separate specific one in the future). In most cases, developers are currently forced to design partial, off-chain and ad-hoc solutions, many times specific to the use cases they are addressing. 

Privacy is a complex subject, but for the purposes of this document, we will describe two different aspects of privacy related to blockchain applications: Confidentiality of Data and Privacy of Transactional Activity.

### 4.3.1. Confidencialidad de Datos
This refers to the ability to keep data private, so unauthorized parties can not see it. This is especially relevant with personal data in the case of natural persons, where “personal data” has the meaning described in the GDPR.

Simple solutions like storing only encrypted data in the blockchain are very delicate, as they can create other problems: if the key to decrypt specific information is lost, the data may not be recovered in the future. Furthermore, if a key is stolen and published, all the data is forever decrypted in the blockchain since the data cannot be altered.

Storing data off-chain and using hashes on-chain can alleviate the second problem, but it comes with its own set of challenges. For example, in Ethereum, all data that is needed to execute a Smart Contract has to be on-chain at the moment of execution (either coming from the global state of the contract or via the payload of the transaction that triggered the execution). The Smart Contract executes inside the EVM and so it does not have access to the data which is stored off-chain at the moment of execution. Given that transaction payloads are stored in the blockchain, they are available to all participants. The same happens with the global state.

As will be seen later, blockchains designed for private consortiums try to solve this problem by storing private data only in the nodes which are party on the transaction, like Quorum, Hyperledger or Corda. However, in most cases this has to be complemented by the off-chain techniques mentioned above. More detailed information of the techniques that can be used is given in the appropriate section further in this document.

### 4.3.2. Privacidad de Actividades Transaccionales
Even though transaction payload and state data could be encrypted, the transactional activity in the blockchain produces metadata. In a public blockchain where the metadata is accessible to all parties, statistical analysis applied to this metadata could make pattern recognition and correlation possible, revealing some information, especially if complemented with external data.

One clear example of this is the “From” and “To” fields in the transaction header in the public Ethereum network. The “From” field is the same for all transactions initiated by a given account, and it is accessible to all participants in the network. Initially, nobody knows the association of a given account with a physical entity in the real world. But if someone, using external information, can derive the association for just one transaction, then they can know the whole transaction history of the associated entity. The same applies to the “To” field, even if it refers to a Smart Contract address.

In a context where members interacting to each other are executing legal transactions (like one company buying mechanical components to its suppliers), the on-chain addresses of each party should be associated to a real entity, and so well known by each party. That means that in a public network like Ethereum, once an entity has transacted with another one, each of the entities know each other’s full transaction history, both in the past and in the future. Even if the actual transaction data is encrypted, there is a lot of information that could be derived (by competitors, for example) from knowing the transactional activities and flows among the parties.

This is not acceptable in a real commercial setting, where the members should have total privacy of their activity with respect to the other members of the network. That is, a member should not be able to see the private activity of any other member if it does not participate itself in that activity. Again, this point does not refer just to data visibility, but also to the actual transactional activity.

Having said that, there may be some legal persons which (eg. for transparency reasons), voluntarily take the decision to make all metadata public (or even the whole data, if it is compatible with the law).

An even stricter scenario is when one of the parties in the transaction is a natural person, due to the required compliance to GDPR.  Even if the personal data is encrypted, leaking transactional metadata which makes statistical analysis possible is not just a commercial decision, but it carries legal and compliance implications.

Another example of leaking metadata is the following: a naive approach to data privacy is encrypting data and using just the hash in the transactions or storing it in the state. If the same hash is reused in many transactions, even if data is encrypted and stored off-chain (like in IPFS), correlation could be performed with the undesirable results just described above. If the source of the encrypted data is personal data, then the system is just pseudonymous and, according to GDPR, the hash in the blockchain should be treated as personal data. And storing personal data in the blockchain where it is accessible to everybody is a very bad idea if not just plain illegal.
As mentioned above, while waiting for  the “holy grail” of privacy-preserving technologies to be implemented natively in public blockchains and made practical to use by the general public, care should be taken to ensure privacy by using other not-so-fancy, but very well know mechanisms coming from the “traditional” world. Some possibilities (and challenges) will be described in a dedicated section below in this document.

# 5. LAS REDES BLOCKCHAIN DEL CONSORCIO PROVADO
On the other side of the “Trust continuum” described in Figure 1, we find the traditional centralized systems and the Private Blockchain Consortiums. Given the different trust requirements in those Private Consortiums, they can implement much more efficient consensus algorithms, without requiring mining and with low and predictable transaction costs.

## 5.1. Una "compensación de confianza" diferente
In public-permissionless networks like Bitcoin or Ethereum, the transacting identities are anonymous (strictly speaking they are pseudonymous, but in practice most of them do not know each other so we can assume they are anonymous), so the task of the system is to achieve with an adequate level of trust that the transactions are valid and that each party will comply with its duties. This is a very difficult task to perform in these conditions, and this is mainly the reason for the poor throughput observed in those public permissionless networks.
 
In private consortiums, the entities transacting have well-known identities, and they are subject to compliance to the law and to regulation. That means that there are lower requirements on “Trustless”, because system trust can be complemented via external mechanisms to the blockchain network. For example, it is expected that at the beginning of the adoption of blockchain technology, the on-chain transactions are covered by standard agreements negotiated and signed in the off-chain world.

The objectives of using blockchain technology in a consortium are normally different than the objectives in a public-permissioned network of unknown participants. Rather than allowing operation among anonymous participants and being able to resist attacks from unknown malicious actors, the main benefit of blockchain technology in a consortium is to make more efficient the operation of the consortium without having to resort to, for example, a Joint Venture to which every participant would have to connect just for technical reasons.

The blockchain technology allows all parties to securely share data and transactional information in a way that avoids costly reconciliations. There are normally very strict governance rules that regulate the sharing of data and ensure the legal enforceability of the transactions that are recorded in the ledger.

By using blockchain technology, entities know that all transactions are, if required, fully traceable and can be easily audited ex post facto, so their incentives to cheat and commit fraud on the blockchain are very low, and in any case could be resolved applying the very well defined governance mechanisms of the consortium or, in extreme cases, via the standard legal mechanisms.

This property of traceability and ex post facto auditability should be enabled by the technical property of “immutability of blockchain data”. In the real world, immutability is not an absolute property, that is, in practice there are degrees of difficulty to modify the data without being noticed.  The question then can be reduced to how to achieve a “good enough” degree of immutability while at the same time achieve sufficient performance and throughput to make the system practical.

In summary, relaxing the level of “system trust” required to function (because we can complement it with external trust among transacting partners), enables us to implement other consensus algorithms which are more efficient and provide greater throughput, while keeping safety at an appropriate level for the purposes of the consortium.

Even in some cases where there are high levels of trust among the participants and the network is secured from external actions, the consortium may decide to implement consensus algorithms which are just CFT ( Crash Fault Tolerant) like Raft, which are more performant than those which are BFT (Byzantine Fault Tolerant).

More details about consensus algorithms will be discussed in the corresponding section below.

## 5.2. Un modelo de incentivación diferente para los nodos operativos
As mentioned at the beginning of the document, in a public-permissionless network there should be an economic incentivisation mechanism for promoting anonymous participants to dedicate expensive computing resources to execute the consensus algorithm required for the operation of the network and ensuring safety.

In those networks the reward system is designed to be extremely short-term, that is, on every block creation event the miner or validator gets rewarded in the cryptocurrency that the network uses. Depending on the actual implementation of the network (eg. PoW, PoS, digital currency units created at launch or not, …) the rewards could be different, but they all share the feature of being very short-term and anonymous (strictly speaking, pseudonymous).

In a private consortium the incentivisation to operate the nodes is completely different, changing to a traditional investment model. The participants in the consortium want to operate the nodes in order to obtain benefits on a longer-term basis. The benefits could come from reduced costs due to increased efficiency, from better service to their customer, or even from new products or services that could be developed jointly.

But in any case, there is no need to use the very short-term incentivisation employed in the public-permissionless networks, so in these blockchains there is no need for embedded cryptocurrencies in order to ensure participation and safety of the network.

This longer-term incentivisation mechanism brings two major benefits:
* The nodes are operated as traditional infrastructure, with low and predictable costs over time. There is not a requirement for transactions fees (unless the members decide to have them because this is their agreed business model). In any case, the costs do not have the highly speculative nature we see currently in public-permissioned networks.
* Allows to use consensus algorithms which are much more efficient and provide higher throughput, and still providing an adequate level of safety.

## 5.3 Un modelo diferente par ala ejecución de transacción
In general, in public-permissionless blockchain networks like Bitcoin and Ethereum there are essentially two mechanisms that ensure the safety property of the network:
1. All transactions are executed and validated in all participating nodes in a deterministic way.
2. There is a consensus algorithm used to ensure that all nodes agree on the same order of transactions, so they are executed in exactly the same order in all the nodes.

For example, in Ethereum the transactions are first validated (via their execution) in the miner/minter nodes, the one node that wins the cryptographic lottery decides the order of transactions in the block, and then all the other nodes in the network execute all the transactions in the block in the order specified by the winner. This is referred to as the “order-execute” model.

Indeed, the existence of an algorithm to reach consensus on the order of transactions is not exclusive to public-permissionless networks and is required in all types of blockchain networks,  though they may differ in the implementation.
However, in private consortiums and in order to achieve privacy, among other things, it is not required that all transactions are executed in all nodes of the network.

For example, in Quorum, private transactions are only executed in the nodes which are privy to the transaction (those specified in the “privateFor” parameter). In addition, the payload of private transactions is only stored in those nodes and is never sent or replicated to any other node in the network, and private transactions can only modify the so-called “private state” which is different in each node and depends on the actual private transactions where each node has participated. Public transactions in Quorum follow exactly the same model as in standard Ethereum.

In contrast to public state, safety of private state data can only be ensured indirectly: even though private transactions are executed in just a reduced number of nodes in the network, the transactions are included in the blocks that are stored in the blockchain in all nodes. The transaction in the block does not include the payload nor the transaction results. A node that did not participate in the private transaction can not verify the transaction by executing it, but all nodes that did participate in the transaction can replay it and given the deterministic nature of the EVM, they can asume that if the initial states were the same

# 6. BLOCK2TRACE UNA BLOCKCHAIN CON PERMISO PÚBLICO
![Alastria in the Trust Continuum](/assets/Alastria%20in%20the%20Trust%20Continuum.jpg)
<p align="center"><b>Fig2. - Alastria in the Trust Continuum.</b></p>

***

In Public-Permissioned networks, the objective is to maximize decentralization and safety, even if this goes to the detriment of scalability. In this context, decentralization typically means the ability to transact anonymously but safely among individuals without the need for any intermediary acting as trusted party. It is often the case that the requirement to eliminate third parties is stronger than the requirement that the system be high-performance so it could be used as a general purpose transaction mechanism.

In Private Consortiums the objectives are generally different, and instead of trying to eliminate third parties at all costs, they try to use blockchain technology to improve efficiency and reduce costs of transaction among the partnets composing the consortium. In many private consortiums, they want a shared database and transaction system so they can eliminate frictions and reduce costs of reconciliation.


As Figure 1 and Figure 2 describe, Alastria tries to be as public as possible, but without the disadvantages associated with public-permissionless networks.

As mentioned before, Alastria is not a Private Consortium but instead is a Public-Permissioned network compatible with regulation (more on this later). At a very high-level, the characteristics of Alastria are the following:
* It’s permissioned, so every participant node has to be identified before it can participate in the network
* No cryptocurrency embedded
* A more efficient consensus algorithm, enabling higher performance and scalability
* Transaction finality in one block, enabling legal validity of executed transactions
* Implements legal identities of all participants

# 7. REQUERIMIENTOS GENERALES SOBRE EL SOFTWARE
## 6.1. Basado en OpenSource de amplia aceptación en el mercado
This is in order to minimize as much as possible any dependencies on any specific vendor. In particular:
1. Alastria will not develop its own blockchain software, but will use a widely used one.
2. Alastria will not incorporate any proprietary components or force to the members to use any proprietary component.
3. The software used by Alastria should be built by an Open Source community as wide and as diverse as possible.

## 7.2. El ecosistema de usuarios del software debe ser lo más amplio posible
This is in order to minimize the risks of using software that will stop being developed in the future. It also makes sure that the innovation rate is high and is also evolving rapidly. In particular:
1. The ecosystem of developers using the software should be as wide as possible.
2. The ecosystem of applications using the software should be as wide as possible.
3. The ecosystem of knowledge about the software should be as wide as possible.

## 7.3. Block2Trace debe basarse en plataformas multisectoriales y de uso general
Alastria has to support all the different use cases that can appear in a multi-industry country blockchain network, so Alastria will avoid any software which is specific to one industry or is too specialised. That means that there may be some very specialized use cases that are not supported directly by Alastria, at least at the beginning. The challenge here is to be able to interoperate between different blockchain networks. One possibility being actively investigated is the ability to run in parallel two (or more) blockchain networks with different technology, to be able to support a wider spectrum of use cases.

## 7.4. Block2Trace permitirá y facilitará el cumplimiento normativo por parte de los miembros, en particular
(The list is in Spanish because we are currently focusing on the specific problems of Spanish regulation).

1. Reglamento General de Protección de Datos (RGPD)
2. Ley de Servicio de Sociedad de la Información y Comercio Electrónico (LSSI)
3. Reglamento de prevención del blanqueo de capitales y de la financiación del terrorismo
4. Normas y recomendaciones del Consejo Nacional de Ciberseguridad

The next section introduces a proposed reference architecture for blockchain systems or DLTs in general (in line with the Reference Architecture being developed in the ISO TC-307) and after that we will discuss the detailed requirements and challenges that a networks like Alastria has to solve.

# 8. ARQUITECTURA DE REFERENCIA DE UNA BLOCKCHAIN
The reference architecture of blockchain and distributed ledger technology consists of five layers, as well as a cross-layer feature set across the layers. They are depicted in the following diagram, and the next sections describe the layers and each of the individual components.

![Reference architecture of a DLT](/assets/Reference%20architecture%20of%20a%20DLT%20-%20overall.jpg)
<p align="center"><b>Fig3. - Reference architecture of a blockchain.</b></p>

## 8.1. Capa de infraestructura
The Infrastructure layer provides the operating environment, including networking, compute and storage components required for the normal operation of a blockchain system. It may be provided as a set of cloud computing resources or it may be provided as on-premises equipment.

### 8.1.1. Almacenamiento de Datos
Physical location to put data for the ledger and other data store requirements. Data Storage function should meet the following requirements:

* can be deployed and used by each node in the peer-to-peer network
* can be deployed distributed or local
* can support appropriate data sovereignty, given that network nodes are in general run and managed by different legal entities
* can provide data writing and query services efficiently, safely and stably
* can provide enough storage space for the growing requirements of the ledger as transactions accumulate with time

Given the characteristics of blockchain systems, probably the most important requirement for the Data Storage function is the sizing requirements in order to support the storage of the historical data for the ledger.

Full nodes typically require the storage of the whole history of the blockchain including the genesis block. Other types of nodes may require less storage, if they assume some reduction in trust for block validation, as it can not be performed against the whole history of the ledger.

These are the associated requirements for the Quorum implementation of Alastria:

| Ref     | Requirement                                           |
|---------|-------------------------------------------------------|
|STOR_001 | What are the storage requirements of Validator nodes? |
|STOR_002 | What are the storage requirements of Regular nodes?   |
|STOR_003 | What is the recommended checkpointing policy in order to reduce the size of the blockchain data, while keeping an appropriate level of trust in the data? |

### 8.1.2. Entorno de tiempo de ejecución (cómputo)
The Runtime environment function provides the execution capabilities (CPU, memory) for the operation of the blockchain system, including but not limited to container technology, virtual machine technology and cloud computing technology. Generally, runtime environments should be provided to each node in the blockchain system.

In general, the fastest the machines of each node in the network, the faster the consensus algorithm can run and he greater the throughput of the network. However, Alastria is starting with Quorum, and in Ethereum-based public-permissioned network like Alastria, some care should be taken on this subject.

In Ethereum, all nodes execute the Smart Contract code associated with all transactions, and the same happens for public transactions in Quorum. In a network running with the IBFT consensus algorithm, a very big throughput on the validator set may require bigger machines in the Regular nodes, to keep up with the network. In other words, it could happen that a given regular node can not execute transactions and commit blocks at the speed at which the validator set generates blocks.

| Ref     | Requirement                                                  |
|---------|--------------------------------------------------------------|
|COMP_001 | What are the CPU and memory requirements of Validator nodes? |
|COMP-002 | What are the CPU and memory requirements of Regular nodes?   |

### 8.1.3. Redes de comunicación
Communication networks are required for the peer-to-peer networking of the DLT system nodes and also for communication between the DLT system and the entities in the user layer and in the non-DLT systems.

Given the network architecture of Alastria, the throughput of the consensus algorithm (IBFT) may be highly dependent of the latency of the communication links among the Validator nodes.

Having dedicated lines would increase throughput, reduce latency and minimize asynchrony. A very well inter-connected validator set may allow heuristics to be applied for much faster consensus algorithm execution. Another example could be using duplicated communication hardware in the validator nodes, which allows for using one card to talk to peer validator nodes and the other card for the rest of the nodes in the network. This way, the validator subnet would be dedicated, and could be protected from DoS attacks.


| Ref     | Requirement                                                  |
|---------|--------------------------------------------------------------|
|COMM_001 | What is the physical architecture of the communications network among validator nodes and what are the minimum requirements for speed, latency and reliability of the communication links among the Validator nodes? How does it affect the consensus algorithm, specifically to the ability of configuring low block making times? |

## 8.2. Capa de plataforma DLT
The DLT Platform layer contains the core functions of the DLT system that can run in a DLT node and which also involves communication between nodes. Key capabilities include:

* Consensus mechanisms which coordinates the data and account records in the ledger between nodes. This consensus mechanism lays the foundation of the DLT system and is probably the function that affects the most to the resulting properties of the the DLT system.

+ Communications between DLT nodes and perhaps systems via events and secure protocols.
Crypto services functions which includes privacy protection, encryption, digital signature and other capabilities to ensure security compliance and tampering resistance of the DLT system.

* Smart contracts running in a secure runtime, that implement the logic running inside the DLT system and updating the ledger data.

The DLT Platform layer connects hardware or network infrastructure provided by the Infrastructure layer, to relevant functional support services in the API layer. In detail, the capabilities supported by the DLT Platform Layer includes:

* Secure runtime
* Smart contract
* Ledger
* Transaction System
* Membership Services
* State Management
* Consensus Mechanism
* Event Distribution
* Crypto Services
* Secure Inter Node Communications

### 8.2.1. Tiempo de Ejecución Seguro
During runtime, a transaction may invoke smart contract functions requiring a secure environment. A secure runtime environment is a hosting environment for server-side DLT business logic.

Different DLTs use different Secure Runtime technologies. For example Ethereum (and so Quorum) uses a Virtual Machine (VM) implementation where all the logic is executed. Hyperledger Fabric uses Docker containers, while others use special hardware to ensure the properties of DLTs and implement a so-called Trusted Execution Environment, or TEE.

For software-based runtimes in a public setting (whether permissionless or permissioned), the runtime should be protected from rogue Smart Contracts or even malicious ones. One mechanism is running the logic inside a metered VM, like in Ethereum or Quorum.

On the other hand, running Smart Contract code inside a container running at native code speed like in Hyperledger Fabric, may be the right approach for private consortiums where the number of nodes is relatively small and the entities are very well known among them, and the code is normally common among all entities and it is certified and tested by all of them.

### 8.2.2. Contrato Inteligente
A Smart contract is a distributed application running on and distributed with the distributed ledger. It represents more the process of agreeing on an outcome than its legal status. Its outcome may or may not be legally binding.

Smart contracts (also termed chaincode, programmable asset or programmable contract) are instantiated as computer programs that execute in a Secure Runtime within the DLT platform of any node in the DLT system, when a user sends a transaction of a particular type to the DLT system.

### 8.2.3. Ledger
A ledger is an information store which keeps a final and definitive record of (business) transactions. A ledger includes data store capabilities. Data Storage function supports writing and query of various types of data, generated during the operation of the DLT system, such as the ledger, transaction information, etc.

The technical implementation of the ledger is often an embedded key-value database, but it can be a  relational database, an external key-value pair database, a file database, and so on. It should support data fragmentation and routing capabilities where database sharding is supported.

Some DLT systems allow the ledger database to be queried externally using the standard tools for that database as they are used in any other type of application.

### 8.2.4. Gestión de Estados
The state management component keeps track of the state of assets which are held on the DLT system, updating that state when new transactions are committed to the ledger.

Normally, the contents of the  state data are not stored in the ledger, but instead the ledger is used to store transactions and pointers to the state data, which is kept separate. The state data is “notarized” in the ledger using hashing technology (usually Merkle Tries).

In the case of Quorum and in order to support privacy, there are two sets of state data: the Public State and the Private State.

Public State is notarized in the ledger and so it is ensured to be globally consistent across all nodes at all times.

However, the Private State may be different across the nodes, depending on which Private Transactions each node has participated on. The assurance of consistency for Private Transactions has to be implicit.

First, the ledger (which is always globally available) stores the hashes of the Private Transactions that have been executed in the corresponding nodes and that have modified the Private State on the nodes which have executed them (each node executes only the transaction to which the node is a party, and not the others).

Thanks to the deterministic property of the transaction execution of the virtual machine, the Private State of each participating node can be implicitly determined to be consistent across the participating nodes, because the modifications to the Private State made by each transaction must have been exactly the same for all nodes executing the transaction.

### 8.2.5. Sistema de Transacciones
The transaction system is the component that manages the addition of transactions to the ledger.

### 8.2.6. Servicios de Membresía
Membership Services are services that manage the identity, privacy, confidentiality and auditability within the DLT system. Membership services only apply to permissioned DLT systems, like Alastria.

In public-permissionless blockchain networks, everything revolves around accounts, which are the entities that can initiate and receive transactions. Given the decentralized philosophy of the system, it is very natural that the transactions and the ledger only store information about the accounts that participate in the transactions, and not, for example, about the actual node that initiated the transaction. In this sense, all nodes in these networks are equal and are just a technical mechanism to participate in the network, much in the same sense as the routers that handle communications among the participants, whose identity is not relevant to the blockchain upper layers.

However, in Alastria and other permissioned networks, we require the management of the identity of the nodes that are being operated by the participants, and that are used to initiate the transactions.

A proper membership service should account for the management of all relevant resources in the network, and that includes the nodes, which have to be permissioned and monitored for compliance to the policies of the consortium. In Quorum, there is a very basic mechanism of permissioning which may be good enough for Private Consortiums, but it needs enhancement for a Public-Permissioned network like Alastria.

Currently, node permissioning is managed via a file that is stored in each participating node and is reloaded and checked every time a new connection request is received in the P2P communications layer. This mechanism has two main disadvantages:

1. Currently, an Alastria participating entity can modify the permissioning file and add the node identities of other entities that are not part of Alastria. Once those non-Alastria entities have their nodes communication directly with the non-compliant node, thanks to the P2P communication protocol of Quorum, they have access to the whole network.
2. Eliminating a node from the permissioning list requires modifying the permissioning file and restarting the node. This implies that eliminating a node from the network requires a restart for all nodes in the network. 

These challenges are formalized as requirements in the following table:

|Ref      | Requirement                                                   |
|---------|--------------------------------------------------------------|
|MEMB_001 | We require a node permissioning mechanism which can not be modified arbitrarily by participating entities.                                   |
|MEMB_002 | We require an un-permissioning mechanism that is dynamic and that does not require a restart of all the nodes in the network.                       |

### 8.2.7. Mecanismo de Consenso
Consensus is a set of rules and procedures that allow the DLT system to maintain and update the distributed ledger and to ensure the trustworthiness of the records in the ledger, that is, their reliability, authenticity and accuracy (this is often referred to as safety). Consensus mechanisms are implementations by which consensus is achieved in DLT systems. There are many alternative consensus mechanisms in use in different DLT systems. Examples of consensus mechanisms include Delegated Proof-of-Stake, Paxos algorithm, Practical Byzantine Fault Tolerance, Proof-of-Authority, Proof-of-Burn, Proof-of-Capacity, Proof-of-ownership, Proof-of-stake, Zero knowledge proof, Proof-of-work.

The current implementation of Quorum in Alastria uses the Istanbul BFT (IBFT) consensus algorithm, and as it is a variant of PBFT its behaviour isf very well documented.

For a Public-Permissioned network like Alastria, IBFT seems much better suited than the current algorithms used (or planned) in public-permissionless networks like PoW or even PoS. The efficiency and transaction throughput that can be achieved are much greater than with those required in public networks. In addition, transaction finality can be deterministic which is a requirement for facilitating legal commercial transactions.

This higher efficiency and throughput in IBFT is achieved by using a reduced set of Validator nodes which are the ones running the consensus algorithm. These nodes are the only ones in the network that decide the blocks in the ledger and which transactions are included and in which order. The rest of the network (Regular nodes), receive the blocks created by the Validator nodes and apply them to the blockchain (of course, after executing and validating the transactions included in the block).

In a Private Consortium, this approach works very well, because it is typically formed by a small number of entities that are very well-known to each other, so the “trustless” requirements are not as high as in public-permissionless networks. In small consortiums, all entities could even run Validator nodes and so the operation of the network is truly decentralized.

For a large Public-Permissioned network like Alastria, there are however some challenges that require novel solutions to them, all revolving around the compromises required to achieve an acceptable throughput but at the same time obtaining a “good enough” level of trust on the system (refer to Figure 2 above).

#### 8.2.7.1. Nodos de confianza y validación en IBFT
The whole network, composed of many entities operating Regular nodes, have to trust that the set of Validator nodes perform their duties as expected. Basically, the entities of Alastria do not necessarily have to trust on each and every of the individual entities running the Validator nodes, but instead they have to trust that the Validator nodes will not collude and collaborate among them to take decisions that will affect adversely to the rest of the nodes (either to individual nodes or to a set of them).

That is, there may be some validator nodes that are not fully trusted by a given entity of Alastria, but if those are less than ⅓ of the total number of Validator nodes, then the whole set can be trusted to perform their duties.

From the point of view of decentralization, this situation is much better than having to rely on a single centralized entity, but nonetheless is less “trustless” than a public-permissionless network. This makes the process of selection of Validator nodes not just a technical one, but a very critical one for the proper functioning of the network and being able to reach the right level of “trustless”.

#### 8.2.7.2. Selección de nodos validadores
For the above reasons, the process of selection of Validator nodes should be decentralized and avoid concentration of power in any single entity or on a reduced group of entities. For example, the set of Validator nodes should reflect diversity across industry sectors and geographies.

| Ref   | Requirement     |
|---------|-------------------------------------------------------------------|
|CONS_001 | What is the policy for determining the entities that operate Validator nodes in Alastria. The technical and operational requirements are not enough, and Alastria needs an additional “political” policy. For example, it would not be desirable that all validator nodes are banks, as this could undermine the trust of the rest of the nodes in the true decentralized properties of the network. That is, diversity has to be maximized and the probability of collusion minimized, while complying with the technical and operational requirements. Additionally, if for example the optimum number of validator nodes is 20 and we have more than 20 entities willing to be a validator node, what is the policy for selecting just 20? As another example, if a better suited validator node (for “political” reasons) asks at some time to become a validator, do we replace an existing one? What is the policy for doing the selection?                     |
|CONS_002 | What are the technical requirements (sizing for CPU, memory, disk) for the Validator nodes. In general, the fastest the machine, the faster the consensus algorithm can run and greater the throughput of the network. However, a very big throughput on the validator set may require bigger machines in the Regular nodes, to keep up with the network. In other words, it could happen that a given regulator node can not execute transactions and commit blocks at the speed at which the validator set generates blocks. |
|CONS_003 | What are the operational requirements for validator nodes? In other words, what are the SLA requirements that entities operating validator nodes have to comply with? This should include procedures and policies to execute when a validator node is detected not working too many times (expulsion and reincorporation to the validator set, off-chain notification and escalation processes, etc).                       |

#### 8.2.7.3. Número de nodos validadores

| Ref     | Requirement                                                       |
|---------|-------------------------------------------------------------------|
|VALID_001 | What is the right number of Validator nodes that Alastria should use? For example, the minimum number for having some BFT protection is 4, and this maximizes performance, but provides the minimum level of safety and decentralization.   |

### 8.2.8. Distribución de Eventos
The event distribution component handles the distribution of events generated within the DLT platform. An example is an event generated by the execution of a smart contract, which might be used by a user application to signal the completion of a transaction to the end user.

### 8.2.9. Servicios Crypto
The Cryptographic Services component provides the DLT system with access to the necessary cryptographic algorithms, either directly or by providing an interface to hardware or software that implements the algorithms. Hash functions and digital signatures are examples of algorithms that are commonly used in DLT systems. Hash functions are often used to protect the ledger from modifications. Any change to information in the ledger will result in a computed hash that is different from the hash that was previously computed and stored for the ledger. A new hash is computed each time a transaction is added to the ledger. Digital signatures ensure that the receiver receives the transactions without intermediate parties modifying or forging the contents of transactions, while also ensuring that the transactions originated from senders (signed with private keys) and not imposters.

### 8.2.10. Comunicación entre nodos segura
The secure inter-node communication component handles communication between nodes over the network, enabling the operation of the distributed ledger. The inter-node protocol, also called the backbone protocol runs via this component.

## 8.3. Capa API
The API layer contains functions that provide reliable and efficient access to the DLT system for applications, users and non-DLT systems, by calling functional components in the DLT Platform layer, and provides unified access and node management. The API layer can enable increased performance by facilitating efficient cache, reliable storage, load balancing, and provide users with reliable and efficient access capabilities. We can distinguish three different types of APIs.

### 8.3.1. Interfaces Externas
Off-chain access services provide secure means to access capabilities outside the DLT system such as trusted data sources or functions.

### 8.3.2. API de Usuario
Application programming interface that provides access to domain specific function meant to accomplish some business purpose (for the business user).

### 8.3.3. API de Administrador
Application programming interface that provides access to administrator and operator functions.

## 8.4. Capa de usuario
User layer contains functions to enable DLT customers to interact with DLT functions, DLT operators, and administrative functions. User layer can also communicate to other layers to provide support for DLT cross-layer functions.

### 8.4.1. Aplicaciones de usuario
User Applications are applications which run separately from the DLT systems that acts as a client to the DLT system, used by users, usually to perform domain specific or applications specific functions.

### 8.4.2. Aplicaciones de administración
Administration Applications are applications which run separately from the DLT systems that acts as a client to the DLT system, used by administrators supporting capabilities to maintain and/or update applications and systems.

## 8.5. Capa de Sistemas No-DLT
La capa de sistemas no DLT contiene sistemas fuera del sistema DLT con los que se comunica un sistema DLT para lograr sus objetivos comerciales. Esto incluye:



### 8.5.1. Oráculo DLT
Un oráculo DLT es un servicio de confianza diseñado para suministrar datos externos a un sistema DLT. Está fuera del alcance de este documento describir en detalle el funcionamiento y la integración de los oráculos en el sistema DLT.

### 8.5.2. Aplicaciones No-DLT
Las aplicaciones que no son DLT son aplicaciones fuera del sistema DLT con las que el sistema DLT se comunica, ya sea para enviar o recibir datos. Un ejemplo es un sistema bancario central conectado a un contrato inteligente que tokeniza el dinero fiduciario.

### 8.5.3. Datos Off Ledger
Los datos Off-Ledger son cualquier almacenamiento de datos fuera del sistema DLT que puede contener datos relacionados con el sistema DLT de alguna manera. Un ejemplo podría ser una base de datos que contenga datos adicionales relacionados con transacciones mantenidas en el Off-Ledger. Los datos Off-Ledger son un componente crítico necesario para implementar funciones adecuadas de privacidad de datos.

## 8.6. Funciones de Capa-Cruzada
Las funciones de capas cruzadas admiten los componentes en todas las capas funcionales. Por ejemplo, la seguridad es necesaria para la capa de usuario, la capa API y la capa de plataforma DLT, por lo tanto, la seguridad es un componente funcional entre capas. Las funciones de capa cruzada también pueden admitir otras funciones de capa cruzada. Las funciones se agrupan en las categorías de Desarrollo, Operaciones y Gestión, Seguridad y Gobernanza y Cumplimiento. Las funciones de capas cruzadas se representan en la siguiente figura y se describen con más detalle en las siguientes secciones.

![Reference architecture of a DLT](/assets/Reference%20architecture%20of%20a%20DLT%20-%20cross%20layer.jpg)
<p align="center"><b>Fig4. - Cross layer functions in a blockchain.</b></p>

### 8.6.1. Desarrollo
Los componentes funcionales de desarrollo respaldan las actividades del desarrollador del sistema DLT, incluido el desarrollo de implementación de aplicaciones y sistemas, la gestión de compilación y la gestión de pruebas.


#### 8.6.1.1. IDE (Entorno de Desarrollo Integrado)
Los componentes funcionales de IDE brindan herramientas para el desarrollo de contratos inteligentes, DLT y aplicaciones relacionadas, incluido el desarrollo de módulos de soporte. Los componentes funcionales de IDE admiten el uso de capacidades proporcionadas por el operador DLT, incluido el acceso a través de API, la gestión de nodos y las capacidades de distribución de eventos. Los IDE permiten el uso de funciones en la API de la capa de la plataforma DLT, así como la capa de infraestructura. El componente IDE admite la generación de metadatos de configuración relacionados con la configuración para el desarrollo del contrato inteligente; admite la preparación o generación de scripts de configuración de contratos inteligentes y componentes utilizados por los sistemas operativos de los operadores y nodos.

#### 8.6.1.2. Gestión de Compilado
Los componentes funcionales de gestión de compilación se utilizan para crear paquetes de software publicables. El paquete puede enviarse al propietario u operador del nodo DLT e implementarse en un entorno de producción. Contiene tanto el software para la implementación de contratos inteligentes como los metadatos de configuración y los scripts de configuración. Las características de gestión de compilación incluyen:

* soporte para la función de paquetes de software de construcción automatizada
* porporcionar una función de compilación automatizada
* proporcionar un mensaje de error cuando se produzca un error durante el proceso de compilación
* implementar la auditoría durante el proceso de construcción
* sistema de compilación que proporciona soporte en varios idiomas

#### 8.6.1.3. Gestión de Prueba
Los componentes funcionales de gestión de pruebas admiten las pruebas de todas las funciones de los sistemas DLT. Los componentes deben generar informes de prueba y proporcionarles el software de implementación del sistema al propietario u operador del nodo. En general, la prueba se realiza en un entorno de prueba independiente especial, que debe ser una simulación del entorno de producción. Sin afectar la producción, el trabajo de prueba también se puede realizar en un entorno de producción. EL operador o socio de DLT debe proporcionar un entorno de prueba.

Los componentes funcionales de gestión de pruebas deben incluir al menos las siguientes funciones:

* los componentes de gestión de pruebas deben admitir la gestión de planes de prueba, casos de prueba, etc
* admite la generación automática de informes de prueba
* cuando la prueba se realiza bajo la integración del entorno de prueba y el entorno de producción
* el entorno de producción no debe verse afectado
* dar soporte a la automatización del proceso de prueba
* proporcionar biblioteca de casos de prueba, funciones de gesti

### 8.6.2. Gestión y Operaciones
Los componentes funcionales de Gestión y Operaciones incluyen un conjunto de funciones de gestión relacionadas con las operaciones, que se utilizan para gestionar y controlar las capacidades DLT proporcionadas al usuario. Los componentes funcionales de Gestión y Operaciones incluyen:

* directorio de servicios
* gestión de incidentes
* gestión de entrega
* gestión de nodos
* gestión de ledger
* monitoreo
* gestión de actualización y versionamiento

#### 8.6.2.1. Directorio de Servicios
La función de Directorio de Servicios proporciona una lista de todas las capacidades de DLT, contratos inteligentes, servicios y/o API de un sistema, operador o nodo de DLT en particular. La lista incluye/se refiere a información técnica sobre la implementación, provisión y operación del contrato inteligente DLT, servicio o API.

#### 8.6.2.2. Gestión de Incidentes
La función de Gestión de Incidentes brinda la capacidad de capturar informes de incidentes y problemas y administrarlos a través del análisis. Los incidentes y problemas pueden ser detectados e informados por el nodo DLT, los operadores DLT o el usuario DLT.

#### 8.6.2.3. Gestión de Entrega
La función de Gestión de Entrega proporciona la función de gestión de entrega del sistema DLT, que se proporciona en forma de implementación del sistema y punto final de acceso. Al mismo tiempo, esta función porporciona los flujos de trabajo necesarios para garantizar que los elementos se proporcionen en el orden correcto.

#### 8.6.2.4. Gestión de Nodos
La función de gestión de nodos proporciona la gestión de la implementación de nodos de la plataforma DLT, incluido el rendimiento y la disponibilidad, normalmente en un sistema lógico o virtual.

#### 8.6.2.5. Gestión de Ledger
La Gestión de Ledger provee el manejo del ledger distribuido.

#### 8.6.2.6. Gestión de Sistemas DLT
La función de Gestión de Sistemas DLT proporciona la gestión de los sistemas DLT especialmente para el rendimiento y la disponibilidad.

#### 8.6.2.7. Monitoreo
Las funciones de monitoreo incluyen herramientas de monitoreo, análisis y automatización que se utilizan para responder a algunos cambios en la plataforma y el entorno. Esto podria incluir responder a cambios en la capacidad del sistema requerida y análisis de errores

Block2Trace ha implementado una primera versiónd de una herramienta de monitorización distribuida que informa sobre diferentes parámetros de cada nodo de la red. Por ejemplo, la herramienta de monitoreo verifica el cumplimiento de las políticas de permisos de todos los nodos de la red.

| Ref      | Requerimiento                                              |
|----------|------------------------------------------------------------|
|MONIT_001 | Validar (o en su defecto sugerir otra opción) que la actual herramienta de monitorización de red implementada en Block2Trace pueda ser utilizada a corto plazo y sugerir mejorar para mejorarla.                                      |

#### 8.6.2.8. Gestión de Actualización y Versionamiento
Las funciones de Gestión de Actualización y Versionamiento incluyen la gestión de bases de código y artefactos de implementación para los nodos y los sistemas DLT.

### 8.6.3. Capacidades de Seguridad
La función de la capa de seguridad es principalmente proporcionar atributos de seguridad como autenticación, autorizarión, confidencialidad, integridad y accesibilidad para todas las capas funcionales del DLT RA y los protocolos entre nodos. Estas características de seguridad se utilizan ampliamente en la autenticación de identidad de usuarios y nodos, diseño de protocolos de transacciones, organización de datos encadenados, encriptacion de canales de comunicación y control de acceso a datos de aplicaciones. La capa de seguridad incluye las siguiente funciones:

* gestión de autenticación e identidad
* gestión de políticas de seguridad
* gestión de acceso
* protección PII

#### 8.6.3.1. Gestión de Autenticación e Identidad
Las funciones de Gestión de Autenticación e Identidad proporcionan un proceso de verificación de identidad del usuario para determinar si el usuario tiene acceso y derechos de uso a un recurso, lo que permite que la política de control de acceso al sistema DLT se realice de manera confiable y eficiente. Los componentes funcionales de Gestión de Autenticación de Identidad incluyen las siguientes características:

* dar soporte al establecimiento de una estrategia de gestión de identidad, determinar si la certificación se basa en información conocida por el usuario, información apropiada por el usuario o características físicas únicas del usuario
* dar soporte al uso de métodos de autenticación de identidad específicos para respaldar las políticas de gestión de identidad
* dar soporte al establecimiento de mecanismos de gestión de la identidad de los usuarios basados en la autenticación de la identidad.

#### 8.6.3.2. Gestión de Políticas de Seguridad
Las funciones de Gestión de Políticas de Seguridad brindan permiso para que los usuarios accedan a un recurso o lo utilicen, y desarrollan un conjunto de reglas que debn seguirse en todas la actividades relacionadas con la seguridad en un área segura. Los componentes funcionales de gestión de políticas de seguridad incluyen:

* función para autorizar a los usuarios a acceder y utilizar recursos
* función para establecer reglas de autenticación y seguridad
* función cuya autorizacióny reglas de seguridad se encuentran controladas po la autoridad de seguridad

#### 8.6.3.3. Gestión de Acceso
El componente de gestión de acceso se utiliza para proporcionar control sobre el acceso a capacidades específicas del sistema DLT. Esto puede incluir controles de acceso aplicados a las diversas interfaces en la capa API.

#### 8.6.3.4. Protección PII
El componente de protección de PII proporciona capacidades para ayudar a brindar la protección adecuada a cualquier PII manejada por el sistema DLT. Esto puede incluir la identificación y clasificación de la PII, la aplicación de cifrado, la gestión del ciclo de vida de la PII (incluida la eliminación anticipada de cualquier PII que ya no sea necesaria), el acceso a la PII para los interesados.

### 8.6.4. Governanza y Cumplimiento
Los componentes funcionales de Governanza y Cumplimiento le permiten al sistema DLR gobernar y auditar características basadas en los requerimientos de governanza y cumplimiento de los dueños y operadores de un nodo DLT. La Governanza puede ayudar a prevenir que las redes DLT se encuentren fuera del marco de las leyes, regulaciones y normas de la industria (como convertirse en la portadora de lavado de dinero, financiamientos ilegales o transacciones criminales). Éstos incluyen las siguientes funciones:

* soporte de supervisión
* soporte de auditoría
* control de governanza
* gestión de políticas

#### 8.6.4.1. Soporte de Supervisión
La función principal del Soporte de Supervisión es cumplir con los requisitos de los cuerpos supervisores para el ambiente, sistema, disponibilidad, recuperación de desastres, operación y mantenimiento del sistema, y el cumplimiento de funciones compatibles en el sistema DLT. Debido a las diferencias entre los supervisores industriales y métodos de supervisión, la profundidad y amplitud de las funciones involucradas son diferentes. Las necesidades específicas incluyen:

* debe tener un sistema de gobierno de supervisión sólido y completo. A través del control previo a la admisión, el control de autoridad en proceso, ex post facto y otros medios técnicos para alcanzar los objetivos de supervisión, garantizar que los registros no puedan ser alterados, sean rastreables y auditables.
* permitir que cuerpos supervisores se unan a la red DLT como uno de los nodos para supervisión inmediate. El nodo supervisor puede monitorear y auditar la integridad de los datos, validez y cumplimiento de procesos en tiempo real, intervenir en transacciones, y detener negocios ilegales. En el caso de Quorum, debe haber un proceso para que las entidades de supervisión puedan obtener los datos de transacciones privadas.
* Los datos y la evidencia relacionada a las actividades de supervisión e intervención deben ser registradas y mantenidas.
* Estableces reglas de governanza de supervisión claras. Dar soporte a las reglas que son supervisadas y gestionadas por personas y no pueden ser implementadas automáticamente mediante la tecnología.
* Dar soporte a las reglas para la organización o personal de gestión para llevar a cabo el gobierno de supervisión de acuerdo con las leyes, regulaciones administrativas, reglas y regulaciones departamentales, fomentar el uso completo de contratos inteligentes y otras tecnologias para dar soporte efectivo a las operaciones de supervisión, y proveer reglas de supervisión para implementaciones automatizadas.
* Almacenar datos y evidencias relacionados a los sistemas, recursos y rendimiento. Estos datos y evidencias incluyen registtros de las actividades y condiciones ambientales operativas de todos los participantes, con la necesidad de ser recolectadas y mantenidas de una manera segura.

#### 8.6.4.2. Soporte de Auditoría
La función del Soporte de Auditoría es principalmente utilizada para lograr auditar control interno, responsabilidad de identificación, rastreabilidad de eventos y otros requerimientos del sistema DLT, que necesita medios tecnológicos efectivos junto con los estándares del sector de negocios para una gestión de auditoría precisa. Los requerimientos específicos incluyen:

* habilitar la realización de auditorías previas, simultáneas y posteriores a las actividades del DLT, establecer indicadores de auditoría tales como auditoría de violación de disciplina, auditoría del sistema de contorl interno, auditoría de desempeño y otros contenidos.
* habilitar a que los auditores de DLT se unan a la red de DLT como uno de los nodos para la auditoría en tiempo real, o permita que el auditor de DLR acceda a datos y pruebas en las redes de DLT a pedido o de manera regular como un tercero fuera de la red de DLT. Fomentar las características trazables e inalterables basadas en la tecnología DLT, realizar verificaciones de tiempo real de registros del objeto auditado y usarlo como evidencia de auditoría.
* habilitar el acoplamiento y las interacciones entre las redes DLT y otros sistemas relacionados, mejorar la eficiencia de la auditoría y la confiabilidad de los resultados de la auditoría.
* habilitar datos y evidencias relacionadas con las actividades de auditoría. Los datos y la evidencia incluyen, pero no son limitados por, registros de actividades y condiciones ambientales operativas de todos los participantes en DLT, registro de vista de auditoría del auditor, procesos de auditoría e información de resultados, y evitar fugas de información de auditoría.

#### 8.6.4.3. Controles de Governanza
Controla las comunicaciones de políticas y las notificaciones de violaciones de políticas y procesos de escalamiento para excepciones y quejas.

#### 8.6.4.4. Gestión de Políticas
La función de la Gestión de Políticas provee definición, actualización y acceso a las políticas para los sistemas DLT y su gestión. Estas políticas incluyen los propios sistemas DLT y su negocio, tecnología, seguridad, privacidad y autenticación. Gestión de políticas en todos los niveles del sistema distribuido.
