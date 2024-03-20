
## Step 1 - listen to question

    Carefully listen to the question. Take notes

## Step 2 - strategize, then divide and conquer

    Ask refining Questions -> Handle the data -> Discuss the components -> Discuss trade-offs


#### Asking refining Questions

    We should ensure that we're solving the right problem.Often it helps to divide the requirements 
    into two groups **Functional Requirements and Non-Functional Requirements.**

1. Requirements that the clients need directly. for example - the ability to send messages in near real-time to friends.
2. Requirements athat are needed indirectly. for example - messaging service performance shouldn't degrate with increasing user load.


#### Handle Data

    We need to identify and understand the data it's characteristics in order to look for 
    appropriate data storage systems and data processing components for the system design.

1. What's the size of the data right now?
2. At what rate is the data expected to grow over time?
3. How will the data be consumed by other subsystems or end users?
4. Is the data read-heavy or write-heavy?
5. Do we need strict consistency of data, or will eventual consistency work?
6. What's the durability of target of the data?
7. What privacy and regulatory requirements do we require for storing or transmitting user data?

#### Discuss the components

    At some level, our job might be perceived as figuring out which components we'll use, 
    where they'll be placed, and how they'll interact with each other.

1. Often abstract away the details of the components as boxes and use arrows to show the interactions between them.
2. It might help to define the user-facing APIs at high level to further understand system data and interaction requirements.

Front-end components, load balancers, caches, databases, firewalls and CDNs are just some examples of system components.

#### Discuss trade-offs

    Remember that there's no one correct answer to a design problem.
        1. Different components have different pros and cons.
        2. Different choices have different costs in terms of money, technical complexity and time to deliver.
        3. Every design has it's weaknesses.As designers, we should be aware of all of them, and 
           we should have a follow-up plan to tackle them.

1. We should point out weaknesses in our design to our interviewer and explain why we haven't tackled them yet.
2. Something is always failing in a big system. We need to integrate fault tolerance and security into our design. 