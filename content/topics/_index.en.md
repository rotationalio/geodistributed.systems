---
title: "Topics"
date: Thu Jun 10 11:16:31 EDT 2021
description: "Key topics of interest in geodistributed systems."
---

*Note: This list of topics of interest is constantly changing, so check back frequently for updates! Suggested readings for each topic will also be expanded and modified.*

## What is a Distributed System?
- Consistency vs Availability
- Data infrastructures of social media apps
- Affordances and limitations of commercial cloud offerings (AWS, Google, etc)

**Suggested Readings**

Ghemawat, Gobioff & Leung (2003) [The Google File System](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)

Corbett, et al (2012) [Spanner: Google’s Globally-Distributed Database](https://www.usenix.org/system/files/conference/osdi12/osdi12-final-16.pdf)

Muralidhar et al. (2014) [f4: Facebook’s Warm BLOB Storage System](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-muralidhar.pdf)

## Consensus Algorithms
- What is consensus?
- Key algorithms: Paxos, Raft, and more
- Implementation challenges

**Suggested Readings**

Lamport, Shostak & Pease (1982) [The Byzantine Generals Problem](https://lamport.azurewebsites.net/pubs/byz.pdf)

Ongaro & Ousterhout (2013) [In Search of an Understandable Consensus Algorithm](http://files.catwell.info/misc/mirror/raft/raft.pdf)

Bilbro & Bengfort (2021) [Concur: An API for Consensus](https://www.slideshare.net/RebeccaBilbro/concur-249308061)

## Machine Learning
- Training models in a distributed system
- Optimizing distributed systems

**Suggested Readings**

Annamualai, et al (2018) [Sharding the Shards: Managing Datastore Locality at Scale with Akkio](https://www.usenix.org/system/files/osdi18-annamalai.pdf)

Bengfort, Xirogiannopoulos & Keleher (2019) [Anti-Entropy Bandits for Geo-Replicated Consistency](https://kelehers.me/papers/get.pl?tag=icdcs018)

Bender, Gebru, McMillian-Major & Mitchell (2021) [On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)

## Data Security and Privacy
- Notable breaches and their causes
- Privacy-first infrastructures

**Suggested Readings**

McCandless & Evans [World's Biggest Data Breaches & Hacks](https://www.informationisbeautiful.net/visualizations/worlds-biggest-data-breaches-hacks/)

## Policy and Legal Issues
- Understanding GDPR (e.g data processors vs consumers)
- Cryptocurrency and the Travel Rule

**Suggested Readings**

Buterin, et al (2013) [The Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)

Linden, Khandelwal, Harkous & Fawaz (2019) [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)

TRISA Working Group (2020) [The TRISA Whitepaper](https://trisa.io/trisa-whitepaper/)

## User Experience
- Balancing UI/UX in distributed systems

**Suggested Readings**

DePalma, Sargent, & Beninatto (2006) [Can’t Read, Won’t Buy](https://insights.csa-research.com/reportaction/305013126/Marketing)

## APIs
- gRPC and Protocol Buffers

**Suggested Readings**

Nally (2020) [gRPC vs REST: Understanding gRPC, OpenAPI and REST and when to use them in API design](https://cloud.google.com/blog/products/api-management/understanding-grpc-openapi-and-rest-and-when-to-use-them)
Bilbro (2021) [What are Protocol Buffers?](https://rotational.io/blog/what-are-protocol-buffers/)