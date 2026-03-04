# Transport-Network

Project Overview
This project implements a knowledge-based transport network using the Python library Owlready2.
The goal is to model a network of cities and flights through an ontology and to perform logical inference in order to determine:
direct flights between cities
indirect flights obtained through intermediate connections
absent routes inferred using the Closed World Assumption (CWA)
The system demonstrates how ontological modeling and non-monotonic reasoning can be used to represent and infer information in a transportation network.
The ontology defines cities and flights as entities and models relationships between them using object properties. Once the network is created, the program performs reasoning to infer indirect routes and determine which routes are not available.

Ontology Structure

The ontology contains two main classes:

City (Citta) – represents a location in the transport network
Flight (Volo) – represents a flight connection between two cities
Two main object properties define flight routes:
LuogoPartenza – indicates the departure city of a flight
LuogoArrivo – indicates the arrival city of a flight
Additionally, two relationships are used to represent connectivity between cities:
volo_diretto – direct connection between two cities
volo_indiretto – indirect connection inferred through an intermediate city
Reasoning Process
The reasoning process occurs in three steps.

1. Direct Flight Creation
Direct connections between cities are defined through a function that creates a flight individual and associates departure and arrival cities.

2. Indirect Flight Inference
Indirect flights are inferred using a simple reasoning rule:
If
City A → City B
and
City B → City C
then
City A → City C (indirect flight)
This step enriches the network by discovering new possible routes without explicitly defining them.

3. Closed World Assumption (CWA)
The project adopts the Closed World Assumption, which means:
If a relationship cannot be inferred from the available knowledge, it is assumed to be false.
Using this principle, the system identifies all city pairs for which no direct or indirect connection exists, marking them as absent routes.
Non-Monotonic Reasoning
The system also demonstrates non-monotonic reasoning.
When a new direct route is added to the network, the inference process is executed again.
This may change previously derived conclusions, meaning that earlier assumptions about missing routes can become invalid once new knowledge is introduced.
For example, when a new flight Trieste → Crotone is added, the network is recomputed and new connections may appear.
