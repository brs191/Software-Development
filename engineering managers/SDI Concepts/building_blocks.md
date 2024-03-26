<!-- TOC -->
  * [1. Domain Name System](#1-domain-name-system)
    * [Important Details](#important-details)
    * [DNS hierarchy](#dns-hierarchy)
    * [DNS caching](#dns-caching)
    * [DNS as a distributed system](#dns-as-a-distributed-system)
    * [Testing](#testing)
  * [2. Load balancers](#2-load-balancers)
  * [3. Databases](#3-databases)
  * [4. Key-Value Store](#4-key-value-store)
  * [5. Content Delivery Network](#5-content-delivery-network)
  * [6. Sequencer](#6-sequencer)
  * [7. Service Monitoring](#7-service-monitoring)
  * [8. Distributed Caching](#8-distributed-caching)
  * [9. Distributed Messaging Queue](#9-distributed-messaging-queue)
  * [10. Publish-Subscribe System](#10-publish-subscribe-system)
  * [11. Rate Limiter](#11-rate-limiter)
  * [12. Blob Store](#12-blob-store)
  * [13. Distributed Search](#13-distributed-search)
  * [14. Distributed Logging](#14-distributed-logging)
  * [15. Distributed Task Scheduling](#15-distributed-task-scheduling)
  * [16. Shared Counters](#16-shared-counters)
<!-- TOC -->
## 1. Domain Name System
    DNS is the Internet's naming service that maps human-friendly domain names to machine-readable IP addresses.
    Typically DNS service is transparent to users. The browser translates the domain name to IP address via DNS Infra.

<kbd> 
    <img src="./img/dns_overview.png">
</kbd>

### Important Details

    - Name servers: DNS isn't a single server. It's a complete infrastructure with numerous servers.
                    DNS servers that respond to the users' queries are called name servers.

    - Resource records: The DNS database stores domain name to IP address mappings in the form of
        record names (RR). The RR is the smallest unit of information that users request from the
        name servers. The 3 important pieces of information are type, name, and value.

| Type  | Description                                                                | Name       | Value          | Example(Type, Name, Value)                               |
|-------|----------------------------------------------------------------------------|------------|----------------|----------------------------------------------------------|
| A     | Provides the hostname to IP address mapping                                | Hostname   | IP address     | (A, relay1.main.educative.io,104,18.2.119)               |
| NS    | Provides the hostname that is the authoritative<br/> DNS for a domain name | Domainname | Hostname       | (NS,educative.io, dns.educative.io)                      |
| CNAME | Provides the mapping from alias to canonical hostname                      | Hostname   | Canonical name | (CNAME, educative.io, server1.primary.educative.io)      |
| MX    | Provides the mapping of mail server from alias to canonoical hostname      | Hostname   | Canonical name | (MX, mail.educative.io, mailserver1.backup.educative.io) |

    
    - Caching: DNS uses caching at different layers to reduce request latency for the user.

    - Hierarchy: DNS name servers are hierarchical form. The hierarchical structure allows DNS to be highly scalable 
        because of its increasing size and query load. 


### DNS hierarchy
    - DNS isn't a single server that accepts requests and responds to queries. It's a complete infrastructure with
        "Name Servers" at different hierarchies. Below are the different types of servers in the DNS hierarchy.
        + DNS resolver: Resolvers initiate the querying sequence and forward requests to the other DNS name servers.
            Typically, DNS resolvers lie within the premis of the user's network. These servers can also be called
            as local or defaults servers. Caching technique is used fo cater DNS queries.

        + Root-level name servers: These servers receives requests from the local servers. Root name servers maintain
            name servers based on top-level domain names, such as .com, .edu, .us, and so on. When a user requests the
            IP address of "docker.io", root-level name servers will return a list of top-level domain (TLD) servers
            that hold the IP addresses of the .io domain.

        + Top-level domain(TLD) name servers: These servers hold the IP addresses of authoritative name servers. The
            querying party will get a list of IP addresses that belong to the authoritative servers of the organization.

        + Authoritative name servers: These are the organization's DNS name servers that provide the IP addresses of the
            web or application servers.

<kbd>
<img src="./img/dns_hierarchy.png">
</kbd>

    - Typically, an iterative query is preferred to reduce query load on DNS infrastructure.


### DNS caching


### DNS as a distributed system

### Test

## 2. Load balancers

## 3. Databases

## 4. Key-Value Store

## 5. Content Delivery Network

## 6. Sequencer

## 7. Service Monitoring

## 8. Distributed Caching

## 9. Distributed Messaging Queue

## 10. Publish-Subscribe System

## 11. Rate Limiter

## 12. Blob Store

## 13. Distributed Search

## 14. Distributed Logging

## 15. Distributed Task Scheduling

## 16. Shared Counters
