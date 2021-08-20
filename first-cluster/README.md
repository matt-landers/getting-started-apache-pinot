# Getting Started with Apache Pinot

1. Review the different components of Pinot
1. Create a Dockerfile
1. Start a Pinot Cluster
1. Create a Schema and Table
1. Ingest Sample Data into Table
1. Query Data from Table

# Anatomy of Apache Pinot

## Tables

⭐️Consist of many Segments that are distributed across n Servers  
⭐️Segments can be replicated for fault tolerance  
⭐️Queries are performed on Tables  
⭐️Tables implement a Schema  
⭐️Can be Offline (loaded via batch processing)  
⭐️Can be Real-time (ingest via real-time events like Kafka)

## Apache Zookeeper

⭐️Metadata service that acts as a distributed filesystem to track cluster state and configuration  
⭐️Apache Helix writes to Zookeeper

## Controllers

⭐️Maintains cluster state with the help of Apache Zookeeper for configuration/metadata and Apache Helix for cluster management  
⭐️Provides endpoints for the REST API, segment uploads, and the Pinot Data Explorer (UI)

## Brokers

⭐️Provides query routing and merging of the results provided by each Server  
⭐️Maintains the query routing table which tracks what Servers host particular segments

## Servers

⭐️Host Segments and Indexes  
⭐️Execute queries provided by Brokers on Segments
