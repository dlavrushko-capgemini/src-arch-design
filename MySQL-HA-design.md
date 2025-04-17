# Architecture Documentation

## Overview
The architecture leverages multiple GCP services to create a highly available MySQL cluster using Orchestrator for topology management and ProxySQL for query routing/load balancing.

The key components include:
* Internal Load Balancer
* Compute Engine
* Cloud SQL

## Components
1. Client: Interacts with the Internal Load Balancer to send requests to the database.
2. Internal Load Balancer: Ensures high availability by distributing incoming traffic across multiple ProxySQL instances.
3. ProxySQL (Compute Engine): Acts as an intermediary between clients and MySQL servers, providing query routing, load balancing, and failover management. Deployed in multiple zones (A and C) for redundancy.
4. Source (Compute Engine): The primary MySQL instance where all write operations are directed. Deployed in multiple zones (A and C) for redundancy.
5. Replica 1 (Compute Engine): A read-only replica of the Source instance, used to offload read traffic from the primary instance. Deployed in Zone B.
6. Orchestrator Database (Cloud SQL): Stores metadata about the MySQL topology managed by Orchestrator.
7. Orchestrator (Compute Engine): Monitors and manages the MySQL replication topology, performing failovers when necessary. Deployed in Zone C.
8. Replication: Ensures data consistency across different zones by replicating data from Source to Replica 1.
9. Heartbeat and Commands: Facilitates communication between Orchestrator instances to monitor health status and execute administrative tasks.
10. Reads/Writes Distribution: Writes are directed to the Source instance, while reads can be distributed between Source and Replica 1 based on configuration.
11. Autoscale: Both ProxySQL and Compute Engine instances hosting Source, Replica 1, and Orchestrator Database have autoscaling enabled to handle varying loads efficiently.
