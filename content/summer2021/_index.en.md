---
title: "Summer 2021"
date: Wed Jun 16 21:52:01 EDT 2021
description: "Details, notes, and questions from the Summer 2021 Reading Group."
---

## Intelligent Distributed Systems Reading Group
The inaugural Intelligent Distributed Systems Reading Group (IDSRG) will run from June 2021 through September 2021. Our goal is to survey the distributed systems literature with an eye towards thinking of how machine learning and data analysis might be used to make these systems more flexible.

## Session 1: The Promise and the Peril of Really Big Models

**Date**:
June 16 8:30PM EDT/June 17 8:30AM HKT

**Reading**:
Bender, et al. (2021) [On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)

**Questions and Discussion Points:**

Model Architectures
- How do 1-shot and 0-shot learning work?
- How important is attention in model training?
- How do multilingual models work?
- What are some good approaches for multiple machine learning models working together?

"Good Models"
- What are some different ways of scoring machine learning models?
- Is there a way to make toxicity scoring work better?
- When is a machine learning model too small? Is there such a thing?

Data Sourcing
- What are the economies of training data?
- If not the internet, where is a better place to get data?

Energy Efficiency
- How can machine learning be made more energy efficient?
- Is there a more efficient way to do consensus (e.g. emergent consensus)?

Distributed Systems
- What is a distributed system?
- What are the foundations of distributed systems?
- What are the roots of consensus algorithms?
- How is reinforcement learning used in distributed systems?
- What is an "intelligent distributed system"?


## Session 2: What Archeology Can Teach Us about Distributed Systems

**Date**:
June 23 8:30PM EDT/June 24 8:30AM HKT

**Reading**:
Lamport, Leslie. "The part-time parliament." Concurrency: the Works of Leslie Lamport. 2019. 277-317.

**Questions and Discussion Points:**

The Consensus Metaphor
- To what extent did Lamport mean to tell the Paxos story in earnest versus an extended allegory?
- How well has the consensus metaphor served the distributed systems community?
- What is concurrency and what does it look like in the context of the part time parliament metaphor?

Consistency of the Distributed Log
- Consistency is about synchronization, which repairs entropy.
- What are the different types of consistency and which is illustrated by Lamport's part time parliament?
- What is the difference between eventual consistency and monotonic reads?
- What is the difference between a "log" and the idea of a distributed ledger? Are these the same?

Paxos & Optimizations
- Do any real world applications use Paxos?
- 2 rounds of communication are required for Paxos, this can be optimized using leader optimization (remove the Prepare phase), ballot optimization, or through optimistic consensus (e.g. Fast Path, ePaxos).


## Session 3: Fantastic Failures and Where to Find Them

**Date**:
June 30 8:30PM EDT/July 1 8:30AM HKT

**Reading**:

Muralidhar, et al. (2014) [f4: Facebook’s Warm BLOB Storage System](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-muralidhar.pdf)

**Questions and Discussion Points:**

Optimization vs. Flexibility
- Is optimization (e.g. using data age, application-level requirements) enough to make a distributed system "intelligent"?
- Where do heuristics about data placement start to break down? For instance, do the rules that work for a big content creator with millions of followers also apply to everyday social media users?
- What features could you use in a distributed system to train a model that would nominate data to be moved from hot to warm or cold storage?
- Could you build a distributed system that would be able to adapt to new blob types, e.g. know how to store them most efficiently?

The UX of Failure
- As users we often experience failures from eventual consistency:
    - Buying plane tickets - when is the purchase final? How do we know?
    - Food ordering apps - the fries gets cold while we're waiting for the system to get consistent.
    - We thought we won the game, but a few seconds later, we're told it was another player.
- We also experience failures in data systems that are in transition:
    - Systems that experience massive (e.g. seasonal) spikes in usage that break consistency.
    - Systems that are being changed to adapt to new market conditions (e.g. conflict between point of sales systems and e-commerce systems).
- We have also experienced correlated failures, such as all of our drives failing simultaneously.

Planning for Failure
- What is the robustness model when failure happens? What's the "intelligent" approach to recover from failure?
- How does data encryption work in a distributed system with correlated failures? What's the relationship between fault tolerance and encryption?


**Related Papers**:

Lu, et al. (2015) [Existential Consensus: Measuring and Understanding Consistency at Facebook](https://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/240-lu.pdf)

Santry, et al. (2004) [Elephant: The File System that Never Forgets](http://www.cs.fsu.edu/~awang/courses/cop5611_s2004/elephant.pdf)


## Session 4: What is "Time" in a Distributed System?

**Date**:
July 7 8:30PM EDT/July 8 8:30AM HKT

**Reading (select one of these)**:

Lamport (1978) [Time, Clocks, and the Ordering of Events in a Distributed System](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)

Corbett, et al (2012) [Spanner: Google's Globally-Distributed Database](https://research.google/pubs/pub39966)


**Questions and Discussion Points:**

"Happened Before"
- In the Lamport paper, the "happened before" relation evolves from a simple relationship between events in the same process (-->) to a relationship between processes happening across a system of clocks (==>) and finally to an even stronger relation that describes distributed processes within and outside the system (**-->**).
- The system of clocks relies on two things to synchronize; first, a mechanism to coordinate via monotonic counters, and a method for arbitrarily ordering system processes (e.g. a global unique identifier for system processes).
- Colloquially we are used to thinking of the word "concurrent" to mean something like "simultaneous". However, Lamport introduces a novel way of thinking about concurrency with respect to the "happened before" relation; namely that two distinct events `a` and `b` are concurrent if `a` did not happen before `b` and `b` did not happen before `a`. From the system's perspective, these two events may as well have happened simultaneously, since we don't have a way to order them.
- How well does the system of clocks scale as system size increases?

Synchronization for the Rich and Famous
- Google's globally distributed system Spanner demonstrates an evolution from the Lamport clock for the age of big data.
- Spanner leverages TrueTime, an API that represents time as an interval and which accounts for variations across geographically remote components of a system. TrueTime is not source available, but there are some details about how it works in this paper and in follow on publications.
- Spanner depends on expensive hardware, including both atomic clocks and GPS devices, apparently collocated with every single rack in the system.
- Spanner is commercially available but does not seem to have much marketing behind it. It is very expensive. Could it be made cheaper by increasing the size of the TrueTime window?
- How well does Spanner work as the system nodes get further apart geographically? Although the phrase "global" comes up a lot in the paper, the examples seem mostly to detail coordination across regions in North America.

To Tick or Not to Tick
- Lamport's paper ends with a proof that physical clocks exist &mdash; meaning clocks that are totally differentiable, with no intervals and no ticks. This was likely Lamport's goal, since at the time he was working to try to devise a computer-based clock for SRI.
- However, 34 years later, the Spanner paper seems to call the existence of physical clocks into question. If Google can't do it without intervals and fancy hardware, can it be done?

**Related Resources**:

SE-Radio (2019) [Episode 377: Heidi Howard on Distributed Consensus](https://www.se-radio.net/2019/08/episode-377-heidi-howard-on-distributed-consensus/)

Kleppman (2020) [Distributed Systems 8.2: Google's Spanner](https://www.youtube.com/watch?v=oeycOVX70aE&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&index=25)


## Session 5: Can Distributed Systems Learn?

**Date**:
July 14 8:30PM EDT/July 15 8:30AM HKT

**Reading**:

Bengfort, et al. (2019) [Anti-Entropy Bandits for Geo-Replicated Consistency](https://kelehers.me/papers/get.pl?tag=icdcs018)

**Questions and Discussion Points:**

Punishment and Reward
- The authors apply reinforcement learning (RL) to optimize anti-entropy in a distributed system.
- Coming up with a good reward function is a common blocker to implementing RL. The clarity of the reward function (rewards for fast, productive sessions) is interesting; this is a great application for RL.

Lessons Learned
- There are a few human-detectable patterns from the RL, such as data center co-location. The model has learned that physical distance is a good measure to improve anti-entropy, but it's not a perfect correlation. 
- It's difficult to tell the differences in performance between the nodes.
- Another result is that not all data centers are created equal, which you can see in the data, especially when they are in the same geographic area e.g. Montreal performs far worse then VA or Ohio in terms of moving data across the network.
- One notable absence is that we didn't see a hierarchy emerge; we expected to see super-spreaders in different regions, but that wasn't prevalent.
-  It seems like there would be a great deal of overlap with routing? There are some very interesting routing algorithms (e.g. traveling salesman) though there are different requirements. One significant difference is that routing is local only vs. the global system the authors experimented on.

Experimental Design
- The authors selected all regions that were available at the time (ex Beijing) with the caveat that some of these regions have many availability zones and they selected A, B, and C.
- The accesses were balanced and consistent, which made for good experimental conditions, but are admittedly not representative of the dynamism of throughput in real applications.
- It was useful to do a thought experiment and think of the system as a phone tree that disseminates downward, which is similar to the super-spreader analogy. The authors controlled for many variables; in the real world, you would most likely see more variability and a heterogeneous topology. If your network optimized for cost, would you show the cheapest nodes vs speed vs compute? Or you could optimize the network for speed or compute.
- With reinforcement learning in general, one issue is: What happens when the world changes? When a system is dynamic? There is some research on this but it often comes down to hard resets; it's often 100-150 time steps to learn the new system, which is not very long, but it doesn't allow for much flexibility.

Achieving Fairness
- One interesting concept is "stomping" i.e. when there are concurrent writes, which gets stomped out? Is there any discussion in the community about equitable stomping? Does it depend on a region that is faster, or more storage? Is there any discussion about how to make it as random as possible beyond Precedence IDs?
- Precedence IDs are human assigned by sys admins and it's an opportunity to inject human bias into the system; e.g. VA > CA > OH etc.; in the system Rotational just deployed, we assigned Precedence IDs using a round-robin method.
- This raises an interesting question: What other ways can human bias be injected into a system that we may not understand or be conscious of?
- In some ways, it's reasonable to assume any intelligent system will have some human bias injected e.g. a system could learn bias based on user engagement (heavy user); we may not be able to remove bias but can we find ways to combat or adapt the system for a bias?
- Randomization may be one way to combat bias; it's an open question if bias is worth thinking about it as long as the system has been consciously set up to combat it.
- Another thought experiment: Imagine a linear network that propagates. There's no way to know how far a write has propagated; so the world could read a write that has a lower precedence but it's the last to know; however, consensus does not allow that to happen; it totally order the writes.

Future Research
- Can you optimize for cost? For example, in Google Cloud, you incur a cost between continents; you really only want one node and not all nodes in the transfers; on the other side of the coin, you want bandwidth; knowing that you'll always have a transfer vector, you can ask questions such as: Can you minimize the transfer cost? Are there intersectional differences inside the cloud? 
- The other thing to think about is user experience. Might we include inconsistencies in the reward function?
- Another possible optimization is objects edited together vs objects edited separately? Can we increase their reciprocal transparency visibility based on this variable? 
- What would happen if we injected chaos; how does that impact the system?
- How could this network be more responsive, more flexible? What happens when accesses change over time? 


## Session 6: Languages of Distributed Systems

**Date**:
July 21 8:30PM EDT/July 22 8:30AM HKT

**Reading**:
gRPC Authors (2021) [What is gRPC?](https://grpc.io/docs/what-is-grpc/)

**Questions and Discussion Points:**

HTTP vs HTTP2: A Major Upgrade
- Much of gRPC's functionality is enabled by HTTP2
- One of the biggest benefits of HTTP2 is it allows for full duplex communication; the web browser can make one request and get all of the data at once (server to client + client to server)
- A lot of things got jammed into HTTP that it wasn't necessarily designed for e.g. web sockets, long-term connections, etc.
- HTTP2 is a binary format vs plaintext in HTTP; a lot of the issues in HTTP are due to plaintext encoding
- Because of its binary format, HTTP2 adds security and massively improves performance e.g. variable inline encoding, compression, better performance management overall, etc.
- HTTP is like the Model T in that Ford didn't know we would build interstate highways; HTTP2 is focused on what the internet will look like in 30 years and now the question is when we'll see it in browsers

API Design
- RESTful APIs are designed to be human-readable whereas gRPC is generally for microservices communication since it is much faster, takes up much less memory, etc.
- One design consideration is human-to-machine communication vs. machine-to-machine or service-to-service communication
- gRPC is a strong contract about how to talk to each other between the data provider and data consumer; it's a very firm and specific but it opens up flexibility for a wide range of business use cases
- gRPC is used widely in microservices e.g. shopping cart management services that talk to inventory management services, etc.
- gRPC allows for pre-processing or "pre-code" to be run before services can talk to each other, which means strict communication protocols e.g. the service has to conform and meet certain requirements before it can talk to another service
- gRPC is useful for advanced services such as moving around large amounts of data between services
- Restful APIs are suited for external programs since they allow for flexibility whereas gRPCs could be better for internal services because they can tightly control design architecture e.g. Google as an example. gRPC is more efficient for asynchronous communication vs REST which is better for sequential communication
- Generally, gRPCs are well-suited for intelligent distributed systems because of its dependence on HTTP2 and its point-to-point communication (that is initiated by one point, not either)
- There are other lower-level libraries like ZeroMQ that could be useful for distributed systems

Protocol Buffers in The Wild
- Probably many of us have used protobufs because that's how Tensorflow works e.g. passing messages between the neural network layers
- Tensorflow has several protobuf and gRPC dependencies; for example, TensorFlow Serving, where models are hosted, is gRPC

Programming Languages & Distributed Systems
- Languages that get closer to the core of how the computer/machine communicates seem to be better for distributed systems
- In contrast, a language like Python is designed to be more human-readable and is less suitable for distributed systems
- While protocol buffers are meant to be language agnostic, gRPC is especially popular with C++ and Golang developers, which makes sense when you think about the built-in coroutines (or Go routines) and channels that are features of those languages. Similar to the reason that Python developers like JSON so much, since it can be seamlessly converted into dictionary objects.

**Related Resources**

- Various [networking pirate patterns in ZMQ](https://zguide.zeromq.org/docs/chapter4/]https://zguide.zeromq.org/docs/chapter4/)
- Podcast interview of [gRPC tech lead Doug Fawley at Google](https://www.se-radio.net/2020/08/episode-421-doug-fawley-on-grpc/)


## Session 7: Takeaways from HotStorage 2021

**Date**:
July 28 8:30PM EDT/July 29 8:30AM HKT

**Reading**:
This week, instead of a shared reading, please register and attend some portion of [HotStorage 2021](https://www.hotstorage.org/2021/), so that we can discuss highlights and takeaways during our usual meeting time.

**Questions and Discussion Points:**

Key Papers
- [Matte et al (2021) "Scalable but Wasteful: Current State of Replication in the Cloud"](https://dl.acm.org/doi/10.1145/3465332.3470882)
- [Adams et al (2021) "Enabling Near-Data Processing in Distributed Object Storage Systems"](https://www.hotstorage.org/2021/2021-slides/ndp_for_obj_stores_slids_adams.pdf)
- [Deshpande et al (2021) "Self-service Data Protection for Stateful Containers"](https://dl.acm.org/doi/10.1145/3465332.3470876)
- [Zhang & Dai (2021) "SentiLog: Anomaly Detecting on Parallel File Systems via Log-based Sentiment Analysis"](https://www.hotstorage.org/2021/2021-slides/SentiLog-SLIDES-Zhang.pdf)
- [Akgun et al (2021) "A Machine Learning Framework to Improve Storage System Performance"](https://www.hotstorage.org/2021/2021-slides/KML-ML-Framework-Storage-OSs-SLIDES-Ibrahim_Umit_Akgun.pdf)

Terms of Interest
- "NDP" - near data processing; a big focus of the conference. Managing hundreds of storage nodes, making the data more distributed
- "CRDTs" - conflict-free replicated datatype
- "LSM tree" - log-structured merge tree
- "SSD" - solid state drive
- "RPO" - recovery point objective
- Blocks vs Rocks - Blocks are uniformly sized vs. rocks, which are more flexible and variable-sized and supports more granularity and more/ different types of file sizes; PebbleDB is smaller rocks
- Shards vs Slices vs Stripes
- "rowhammering"
- PFS: why no global IDs?
- Two-phase backup scheduler

Types of Consistency
- We mostly have been talking about eventual consistency so far. Consistency is about what users can expect from a system.
- As you move up the spectrum toward strong consistency, the more coordination is needed i.e there is a lot of message traffic, which often leads to degraded performance, which runs into the CAP problem.
- There is a spectrum from weak to strong consistency:
    - "weak consistency": No guarantee that systems will converge
    - "eventual consistency" (and "strong eventual consistency"): If you stop writing, the system will eventually become consistent.
    - "causal consistency": guarantees all processes observe causally-related operations in a common order.
    - "sequential consistency": Ordered operations that are observable e.g. the Lamport paper
    - "strong consistency" (aka linearizability): For every person on earth there is a single order of operations. Spanner is probably the closest example we've looked at so far.

New Technologies
- Databases, File Systems, and Object Storage
    - CockroachDB
    - YugaByte
    - RocksDB
    - PebbleDB
    - ElmerFS
    - Lustre and BeeGFS (Parallel file systems)
    - Minio
    - Ceph
    - Storj.io
    - etcd

- Consensus Algorithms
    - Raft
    - Multi-Paxos
    - EPaxos
    - Pig Paxos

- Libraries
    - DeepLog

General Questions
- *Why is it called "Hot Storage"?*
    - Originally called "Hot Topics in Storage Systems"; follows from a series of "Hot" topics in computer science such as security, networking, etc.
    - The name Hot Storage is also connected to electrical engineering and it's relation to storage systems i.e. thousands of spinning discs
    - Attracts a lot of interesting domains e.g. bioinformatics, DNA storage systems, ML and optimization - very interdisciplinary

- *What's with the emphasis on flash storage?*
    - Might have to do with the hardware available to the participants; best way to experiment and try out new ideas and configurations.

- *Is it common for there to be so many theoretical papers (compared to ones with experimental results)?*
    - Hot Storage has become a primary publishing venue for grad students; it gives researchers the opportunity to share/ discuss research even if they don't have complete results yet

- *Not a lot of representation from the big cloud folks - Google, Amazon, that other one. Why is that?*
    - FAST is the larger conference counterpart to Hot Storage; a lot of big tech companies (Twitter, Google, FB) sponsor or attend FAST



## Session 8: What is a "File" Anyway?

**Date**:
August 4 8:30PM EDT/August 5 8:30AM HKT

**Reading**:
Rosenblum & Osterhout (1991) [The Design and Implementation of a Log-Structured File System](https://people.eecs.berkeley.edu/~brewer/cs262/LFS.pdf)

**Questions and Discussion Points:**

tbd


## Session 9: tbd

**Date**:
August 11 8:30PM EDT/August 12 8:30AM HKT

**Reading**:
tbd

**Questions and Discussion Points:**

tbd

## Session 10: tbd

**Date**:
August 18 8:30PM EDT/August 19 8:30AM HKT

**Reading**:
tbd

**Questions and Discussion Points:**

tbd


## Farewell and Onto New Things...

**Date**:
August 25 8:30PM EDT/August 26 8:30AM HKT

**Reading**:
tbd

**Questions and Discussion Points:**

tbd