# Table of Contents
1. back-of-the-envelope calculations
2. Types of Data Centers
3. Standard numbers to remember
4. Requests estimation

## back-of-the-envelope calculations
    A distributed system has compute nodes connected via a network. There are wide variety of available
    compute nodes and they can be connected in many different ways.

    Back-of-the-envelope calculations helps us to ignore the nitty-gritty details of the system (at least
    at the design level) and focus on more important aspects.


some examples of a back-of-the-envelope calculation could be
- The number of concurrent TCP connections a server can support
- The number of requests per second (RPS) a web, database, or cache server can handle
- The storage requirements of a service

Choosing an unreasonable number of such calculations can lead to a flawed design. Below concepts helps
us arrive a reasonable calculations.

## Types of data center servers
    Data centers don't have a single type of server. Enterprise solutions use commodity hardware to
    save cost and develop scalable solutions.

![img.png](./img/datacenters_types.png)

- **Web servers** 


    Web servers are the first point of contact after load balancers. Typical data centers have racks
    full of web servers t hat usually handle API calls from the clients.

    1. These servers requires good computational resources.
    2. Depending on the service that's offered, the memory and storage resources are small to medium.
    3. Web servers mostly server static content to the client

**Application servers**


    1. Application servers run the core application software and business logic.
    2. Depending on the application logic, these servers require extensive computation and storage resources.
        ex - Facebook application servers uses upto 256GB RAM and two types of storage -- traditoinal
             rotating disks and flash -- with a capacity of up to 6.5TB.

**storage servers**

    With the explosive growth of Internet users, the amount of data stored by giant servers has multiplied.
    For instance, youtube uses the following datastores:
        1. Blob storage for its encoded videos.
        2. A temporary processing queue storage that can hold a few hunderd hours of video content
            uploaded dialy to YouTube for processing
        3. Specialized storage called Bigtable for storing a large number of thumbnails of videos.
        4. RDBMS for users and vidoes metadata (comments, likes, user channels, and so on)

    Facebook numbers that were open-sourced back in the day -
        
        | Component         | Count                     |
        |-------------------|---------------------------|
        | Number of Sockets | 2                         |
        | Processor         | Intel Xeon X2686          |
        | Number of Cores   | 26 cores (72 H/W Threads) |
        | RAM               | 256 MB                    |
        | Cache (L3)        | 45 MB                     |
        | Storage Capacity  | 15 TB                     |


**standard numbers to remember**
    
    Important Latencies
    
    | Componnent                                                     | Time (nano seconds)            |
    |----------------------------------------------------------------|--------------------------------|
    | L1 cache reference                                             | 0.9                            |
    | L2 cache reference                                             | 2.8                            |
    | L3 cache reference                                             | 12.9                           |
    | Main Memory reference                                          | 100                            |
    | Compressed 1KB with Snzip                                      | 3,000 (3 micro-seconds)        |
    | Read 1MB sequentially from memory                              | 9,000 (9 micro-seconds)        |
    | Read 1 MB sequentially from SSD                                | 200,000 (200 micro-seconds)    |
    | Round Trip within same datacenter                              | 500,000 (500 micro-seconds)    |
    | Read 1 MB sequentially from SSD<br/> with speed ~1GB/sec <br/> | 1000,000 (1 milli-seconds)     |
    | Disk seek                                                      | 4000,000 (4 milli-seconds)     |
    | Read 1 MB sequentially from disk                               | 2000,000 (2 milli-seconds)     |
    | Send package SF->NYC                                           | 71,000,0000 (71 milli-seconds) |


    Important Rates
    
    |                                |             |
    |--------------------------------|-------------|
    | QPS handled by mySQL           | 1000        |
    | QPS handled by key-value store | 10,000      |
    | QP handled by cache server     | 100,000-1 M |


**Request estimation**

    Within a server, there are limited resources and depending on the type of client requests, different resources
    can become bottleneck.

    Assumptions - 
        1. Our server is a typical server with pretty default config as below.
        2. OS and other services consumed a total of 16GB of RAM.
        3. Each worker consumes 300 MBs of RAM storage to complete a request.
        4. For simplicaity, we assume that the CPU obtains data from the RAM. (caches always a hit)
        5. Each CPU-bound request takes 200ms, whereas a memory-bound request takes 50ms

    CPU-bound - 
        CPU bound RPS = (Number of CPU threads, which are also called by hardware threads) * 1/(time each task takes to complete)
        RPS_CPU = Num_CPU x (1/Task_time)

        ex = RPScpu = 72 * 1/200 ms = 360 RPS

    
    Memory-bound -
        Memory bound RPS = (Total size of RAM/Worker Memory) * 1/(A worker in memeroy that manages a request)
        RPS_Memory = (RAMsize/WORKERmemory) * (1/TASKtime)

        ex = RPSmemory = 240GB/300MB * 1/50ms = 16,000 RPS

    A server receives both the CPU-bound and memory-bound requests. Considering the case that half of the
    requests are CPU-bound and the other half memory-bound --
        360/2 + 16,000/2 = 8,180 == 8,000 RPS

**Exercise**

Number of servers required for a Twitter-like server -

    Assumptions:
        - There are 500 Million (M) daily active users (DAU).
        - A single user makes 20 requests per day on average.
        - Recall that a singler server can handle 8,000 RPS.
---- TODO ----