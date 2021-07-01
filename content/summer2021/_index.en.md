---
title: "Summer 2021"
date: Wed Jun 16 21:52:01 EDT 2021
description: "Details, notes, and questions from the Summer 2021 Reading Group."
---

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
- It optimization (e.g. using data age, application-level requirements) enough to make a distributed system intelligent?
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
- We have also experience correlated failures, such as all of our drives failing simultaneously.

Planning for Failure
- What is the robustness model when failure happens? What's the "intelligent" approach to recovery from failure?
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

tbd
