# Block2Trace Core Technical Platform
## Requirements and challenges for a country blockchain network

<!-- TOC -->

- [Alastria Core Technical Platform](#alastria-core-technical-platform)
    - [Requirements and challenges for a country blockchain network](#requirements-and-challenges-for-a-country-blockchain-network)
1. [Objective](#1-objective)
2. [Introduction](#2-introduction)
3. [General characteristics of the main blockchain technologies](#3-general-characteristics-of-the-main-blockchain-technologies)
3. [The Public-Permissionless blockchain networks](#3-the-public-permissionless-blockchain-networks)
    - 3.1 [The problem of Scalability of Public-Permissioned blockchains](#31-the-problem-of-scalability-of-public-permissioned-blockchains)
    - 3.2 [The problem of Transaction Costs: High and Volatile](#32-the-problem-of-transaction-costs--high-and-volatile)
    - 3.3 [The problem of Privacy](#33-the-problem-of-privacy)
                - 3.3.1 [Confidentiality of Data](#331-confidentiality-of-data)
                - 3.3.2 [Privacy of Transactional Activity](#332-privacy-of-transactional-activity)
4. [THE PRIVATE CONSORTIUM BLOCKCHAIN NETWORKS](#4-the-private-consortium-blockchain-networks)
    4.1 [A different “Trust trade-off”](#41-a-different-trust-trade-off)
    4.2 [A different incentivisation model for operating nodes](#42-a-different-incentivisation-model-for-operating-nodes)
    4.3 [A different Transaction execution model](#43-a-different-transaction-execution-model)
5. [ALASTRIA: A PUBLIC-PERMISSIONED BLOCKCHAIN NETWORK](#5-alastria--a-public-permissioned-blockchain-network)
6. [GENERAL REQUIREMENTS ABOUT THE SOFTWARE](#6-general-requirements-about-the-software)
    6.1 [Based on OpenSource of wide acceptance in the market](#61-based-on-opensource-of-wide-acceptance-in-the-market)
    6.2 [The ecosystem of users of the software should be as wide as possible](#62-the-ecosystem-of-users-of-the-software-should-be-as-wide-as-possible)
    6.3 [Alastria should be based on general-purpose and multi-industry platforms](#63-alastria-should-be-based-on-general-purpose-and-multi-industry-platforms)
    6.4 [Alastria will allow and facilitate regulatory compliance by the members, in particular:](#64-alastria-will-allow-and-facilitate-regulatory-compliance-by-the-members--in-particular)
7. [REFERENCE ARCHITECTURE OF A BLOCKCHAIN](#7-reference-architecture-of-a-blockchain)
    7.1 [Infrastructure layer](#71-infrastructure-layer)
        7.1.1 [Data Storage](#711-data-storage)
        7.1.2 [Runtime Environment (Compute)](#712-runtime-environment-compute)
        7.1.3 [Communication Networks](#713-communication-networks)
    7.2 [DLT Platform layer](#72-dlt-platform-layer)
        7.2.1 [Secure Runtime](#721-secure-runtime)
        7.2.2 [Smart Contract](#722-smart-contract)
        7.2.3 [Ledger](#723-ledger)
        7.2.4 [State Management](#724-state-management)
        7.2.5 [Transaction System](#725-transaction-system)
        7.2.6 [Membership Services](#726-membership-services)
        7.2.7 [Consensus Mechanism](#727-consensus-mechanism)
            7.2.7.1 [Trust and Validator nodes in IBFT](#7271-trust-and-validator-nodes-in-ibft)
            7.2.7.2 [Selection of Validator nodes](#7272-selection-of-validator-nodes)
            7.2.7.3 [Number of Validator nodes](#7273-number-of-validator-nodes)
        7.2.8 [Event Distribution](#728-event-distribution)
        7.2.9 [Crypto Services](#729-crypto-services)
        7.2.10 [Secure Inter-Node Communication](#7210-secure-inter-node-communication)
    7.3 [API layer](#73-api-layer)
        7.3.1 [External Interfaces](#731-external-interfaces)
        7.3.2 [User API](#732-user-api)
        7.3.3 [Admin API](#733-admin-api)
    7.4 [User layer](#74-user-layer)
        7.4.1 [User Applications](#741-user-applications)
        7.4.2 [Administration Applications](#742-administration-applications)
    7.5 [Non-DLT Systems Layer](#75-non-dlt-systems-layer)
        7.5.1 [DLT Oracles](#751-dlt-oracles)
        7.5.2 [Non DLT Applications](#752-non-dlt-applications)
        7.5.3 [Off Ledger Data](#753-off-ledger-data)
    7.6 [Cross-layer functions](#76-cross-layer-functions)
        7.6.1 [Development](#761-development)
            7.6.1.1 [IDE (Integrated Development Environment)](#7611-ide-integrated-development-environment)
            7.6.1.2 [Build Management](#7612-build-management)
            7.6.1.3 [Test Management](#7613-test-management)
        7.6.2 [Management and Operations](#762-management-and-operations)
            7.6.2.1 [Service directory](#7621-service-directory)
            7.6.2.2 [Incident Management](#7622-incident-management)
            7.6.2.3 [Delivery Management](#7623-delivery-management)
            7.6.2.4 [Node Management](#7624-node-management)
            7.6.2.5 [Ledger Management](#7625-ledger-management)
            7.6.2.6 [DLT System Management](#7626-dlt-system-management)
            7.6.2.7 [Monitoring](#7627-monitoring)
            7.6.2.8 [Update and Version Management](#7628-update-and-version-management)
        7.6.3 [Security capabilities](#763-security-capabilities)
            7.6.3.1 [Authentication and Identity Management](#7631-authentication-and-identity-management)
            -7.6.3.2 [Security Policy Management](#7632-security-policy-management)
            7.6.3.3 [Access Management](#7633-access-management)
            7.6.3.4 [PII Protection](#7634-pii-protection)
        7.6.4 [Governance and Compliance](#764-governance-and-compliance)
            7.6.4.1 [Supervisory Support](#7641-supervisory-support)
            7.6.4.2 [Audit Support](#7642-audit-support)
            7.6.4.3 [Governance Controls](#7643-governance-controls)
            7.6.4.4 [Policy Management](#7644-policy-management)

<!-- /TOC -->

# 1. Objective
This document describes the requirements and challenges for a country blockchain network like Alastria. While the document tries to be as technology-agnostic as possible, there are subjects where we have to focus on a given technology, and when this is the case, we discuss the initial implementation using Quorum. However, the intention is to include specific analyses for other technologies like Hyperledger.  This document is live and continuously evolving, describing the current situation of the technology with respect to the requirements and the challenges that have to be solved.

# 2. Introduction

Alastria is a Spanish nonprofit association with the objective to create the first multi-industry national blockchain network, to support transactions with full legal validity, and with appropriate levels of privacy.

We are currently more than 250 companies and institutions from different sectors like banking, telco, energy, insurance, law firms, technology and services companies, research institutions, universities, etc.. The association is growing, because it is inclusive and open to anybody who would like to collaborate and participate in the initiative.

The associates of Alastria are collaborating with each other in the definition, deployment, operation and maintenance of the infrastructure, but will compete with each other in the specific use cases built on top of the network.

Being a country-wide blockchain network, Alastria is neither a public-permissionless network nor a private consortium. Alastria shares some of the properties of both types of networks, but it has some requirements of its own. This document is structured as follows:
* The first two sections describe the general characteristics of Public-Permissionless and Consortium blockchains and the problems that they present for a network like Alastria
* Then we describe the specific requirements of Alastria, using as a scheme and guiding theme a general Reference Architecture of blockchains systems

# 3. General characteristics of the main blockchain technologies
