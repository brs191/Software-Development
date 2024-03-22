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



