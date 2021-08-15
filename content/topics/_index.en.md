---
title: "Topics"
date: Thu Jun 10 11:16:31 EDT 2021
description: "Key topics of interest in geodistributed systems."
---

*Note: This list of topics of interest is constantly changing, so check back frequently for updates! Suggested readings for each topic will also be expanded and modified. Please report expired links [here](https://github.com/rotationalio/geodistributed.systems/issues).*

## What is a Distributed System?
- Consistency vs Availability
- Weak, Strong, and Eventual Consistency

**Suggested Readings**

Ousterhout & Rosenblum (1991) [The Design and Implementation of a Log-Structured File System](https://people.eecs.berkeley.edu/~brewer/cs262/LFS.pdf)

Terry, et al. (1994) [Session Guarantees for Weakly Consistent Replicated Data](http://www.cs.cornell.edu/courses/cs734/2000FA/cached%20papers/SessionGuaranteesPDIS_1.html)

Terry, et al. (1995) [Managing Update Conflicts in Bayou, a Weakly Connected Replicated Storage System](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p172-terry.pdf)

Petersen, et al. (1997) [Flexible Update Propagation for Weakly Consistent Replication](https://dl.acm.org/doi/10.1145/268998.266711)

Glendenning, et al. (2011) [Scalable Consistency in Scatter](https://homes.cs.washington.edu/~tom/pubs/scatter.pdf)

Bailis, et al. (2012) [Probabilistically Bounded Staleness for Practical Partial Quorums](http://vldb.org/pvldb/vol5/p776_peterbailis_vldb2012.pdf)

Hewitt, et al. (2012) [The Actor Model (everything you wanted to know...)](https://youtu.be/7erJ1DV_Tlo)

Bernstein, et al. (2014) [Orleans: Distributed virtual actors for programmability and scalability](https://www.semanticscholar.org/paper/Virtual-Actors-for-Programmability-and-Scalability[…]stein-Bykov/3f41b90454cbf73ce284917ae58678bc86d6ee76?p2df)

Raju, et al. (2017) [PebblesDB: Building Key-Value Stores using Fragmented Log-Structured Merge Trees](https://dl.acm.org/doi/abs/10.1145/3132747.3132765)

## Distributed Systems in the Wild
- Data infrastructures of social media apps
- Affordances and limitations of commercial cloud offerings (AWS, Google, etc)

**Suggested Readings**

Ghemawat, et al. (2003) [The Google File System](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)

Corbett, et al. (2012) [Spanner: Google’s Globally-Distributed Database](https://www.usenix.org/system/files/conference/osdi12/osdi12-final-16.pdf)

Muralidhar, et al. (2014) [f4: Facebook’s Warm BLOB Storage System](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-muralidhar.pdf)


## Consensus Algorithms
- What is consensus?
- Key algorithms: Paxos, Raft, and more
- Implementation challenges

**Suggested Readings**

Lamport, et al. (1982) [The Byzantine Generals Problem](https://lamport.azurewebsites.net/pubs/byz.pdf)

Lamport (2001) [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)

Ongaro & Ousterhout (2013) [In Search of an Understandable Consensus Algorithm](https://www.usenix.org/system/files/conference/atc14/atc14-paper-ongaro.pdf)

Bilbro & Bengfort (2021) [Concur: An API for Consensus](https://www.slideshare.net/RebeccaBilbro/concur-249308061)

## Machine Learning
- Training models in a distributed system
- Optimizing distributed systems

**Suggested Readings**

Annamualai, et al. (2018) [Sharding the Shards: Managing Datastore Locality at Scale with Akkio](https://www.usenix.org/system/files/osdi18-annamalai.pdf)

Bender, et al. (2021) [On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)

Bengfort, et al. (2019) [Anti-Entropy Bandits for Geo-Replicated Consistency](https://kelehers.me/papers/get.pl?tag=icdcs018)

Hilprecht & Binnig (2021). [One Model to Rule them All: Towards Zero-Shot Learning for Databases](https://arxiv.org/pdf/2105.00642.pdf)

Schmied et al. (2021). [Towards a General Framework for ML-based Self-tuning Databases](https://arxiv.org/pdf/2011.07921.pdf)

Somashekar & Gandhi (2021). [Towards Optimal Configuration of Microservices](https://www3.cs.stonybrook.edu/~anshul/euromlsys21_opt.pdf)

Zaharia, et al. (2012) [Resilient Distributed Datasets: A Fault-Tolerant Abstraction for In-Memory Cluster Computing](https://www.usenix.org/system/files/conference/nsdi12/nsdi12-final138.pdf)

## Energy Efficiency
- How can distributed systems be made more energy efficient?
- Is there a more efficient way to do consensus (e.g. emergent consensus)?

**Suggested Readings**

Bender, et al. (2021) [On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)

Charapko (2021) [Scalable but Wasteful, Or Why Fast Replication Protocols are Actually Slow](http://charap.co/scalable-but-wasteful-or-why-fast-replication-protocols-are-actually-slow/)

## Data Security and Privacy
- Public key cryptography
- Symmetric and asymmetric encryption
- Notable breaches and their causes
- Privacy-first infrastructures

**Suggested Readings**

Diffie & Hellman (1976) [New Directions in Cryptography](https://ee.stanford.edu/~hellman/publications/24.pdf)

Li, et al. (2004) [Secure Untrusted Data Repository (SUNDR)](http://css.csail.mit.edu/6.858/2020/readings/sundr.pdf)

Nakov (2019) [Practical Cryptograpy for Developers. Chapter 6 - Encryption: Symmetric and Asymmetric](https://cryptobook.nakov.com/encryption-symmetric-and-asymmetric)

McCandless & Evans (2021) [World's Biggest Data Breaches & Hacks](https://www.informationisbeautiful.net/visualizations/worlds-biggest-data-breaches-hacks/)


## Policy and Legal Issues
- Understanding GDPR (e.g data processors vs consumers)
- Cryptocurrency and the Travel Rule

**Suggested Readings**

Buterin, et al. (2013) [The Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)

Linden, et al. (2019) [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)

TRISA Working Group (2020) [The TRISA Whitepaper](https://trisa.io/trisa-whitepaper/)

## User Experience
- Balancing UI/UX in distributed systems
- Localization (l10n) and internationalization (I18n)

**Suggested Readings**

DePalma, et al. (2006) [Can’t Read, Won’t Buy](https://insights.csa-research.com/reportaction/305013126/Marketing)

Scott (2013) [Characters, Symbols and the Unicode Miracle](https://youtu.be/MijmeoH9LT4)

Patch (2014) [Unicode Beyond Just Characters: Localization with the CLDR](https://youtu.be/DcPpUnlENAs)

The GNU gettext authors [GNU gettext utilities](https://www.gnu.org/software/gettext/manual/gettext.html)

CLDR [Unicode Common Locale Data Repository](http://cldr.unicode.org/index)

## Languages and APIs
- What languages are best suited to distributed systems?
- gRPC and Protocol Buffers

**Suggested Readings**

Bal, et al. (1989) [Programming Languages for Distributed Computing Systems](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.145.7873&rep=rep1&type=pdf)

Ferreira, et al. (2020) [Programming Languages for Distributed Systems and Distributed Data Management](https://drops.dagstuhl.de/opus/volltexte/2020/11858/pdf/dagrep_v009_i010_p117_19442.pdf)

gRPC Authors (2021) [Introduction to gRPC](https://grpc.io/docs/what-is-grpc/introduction/)

Nally (2020) [gRPC vs REST: Understanding gRPC, OpenAPI and REST and when to use them in API design](https://cloud.google.com/blog/products/api-management/understanding-grpc-openapi-and-rest-and-when-to-use-them)

Bilbro (2021) [What are Protocol Buffers?](https://rotational.io/blog/what-are-protocol-buffers/)