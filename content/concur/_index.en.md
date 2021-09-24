---
title: Concur
---

## Consensus is Not One-Size-Fits-All
One of the things we wanted to communicate with the Yellowbrick project is that there is no one “best” machine learning model, only a set of best practices for finding the best model for a given dataset. We believe the distributed systems community has a similar problem; everyone is looking for the golden consensus algorithm, but there’s no silver bullet. What makes sense for Google isn’t best for Facebook; what’s used at Twitter isn’t ideal for Netflix. Different systems need different consensus solutions.

Together we have implemented many of the published algorithms -- Raft, Mencius, ePaxos. We are surprised to see how many elements these implementations have in common. What this tells us is that there’s a common framework that can be abstracted out of these implementations and used to make consensus more convenient for students, researchers, and developers like us.

Concur is a new open source project designed to give the systems community a way to discover the best algorithm for each context. The Concur API abstracts and uncouples the primary system components of a distributed system — messaging, peer management, decision making, and execution — into an interface, allowing users to compose systems from common building blocks. Students can use Concur to compare algorithms such as Raft, ePaxos, or Mencius. Researchers can use the API to quickly build experiments and test out new configurations. Finally, developers can use the Concur API to prototype production systems that are easier to reason about, diagnose, and tune.