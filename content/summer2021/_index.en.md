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

tbd

