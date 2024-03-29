---
layout: post
title: "Will Quantum Software Eat the World?"
date: 2019-07-14 11:12:21 -0500
categories: blog
comments: true
---
The emergence of quantum computing hardware in recent years has produced an explosion of quantum startup businesses hoping to cash in on the burgeoning industry. At present, there are [well over 100 private companies focused on quantum computing](https://quantumcomputingreport.com/players/privatestartup/), not counting the large public companies, government entities, and academic groups who are also pouring resources into the technology. While this avalanche of funding, combined with the lack of any practical applications at the moment, leads many to worry about a coming ["quantum winter"](https://www.ryanshaffer.net/blog/2019/07/07/why-quantum-winter-is-not-coming.html), I want to explore a different aspect here: what does the interplay between quantum hardware and quantum software look like, and how can we expect this to evolve over time? Or, to borrow a phrase from Marc Andreessen, will quantum software [eat the world](https://a16z.com/2011/08/20/why-software-is-eating-the-world/)?

<img src="/images/quantum-circuit.jpg" alt="Quantum circuit" width="490" /> 

## Technology strategy: software and hardware

A few years ago, I took a detailed look at [the scenarios in which technology companies decide to build complementary hardware and software products](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=SRrFQ-gAAAAJ&citation_for_view=SRrFQ-gAAAAJ:MXK_kJrjxJIC), and when these efforts are most likely to succeed. In general, the strategy pays off when the software product is:

<p class="has-text-align-center">
  <strong>(a)</strong> essential to the use of the hardware product, that is, either it is the only software in existence, or it is fundamentally better than other existing software options (think of early mainframe computers),<br /><strong>(b)</strong> tightly integrated with a piece of specialized hardware to perform a function more efficiently than more general-purpose devices can accomplish (think of iPod and iTunes in the early days), and/or<br /><strong>(c)</strong> core to the business, with the hardware product serving as a funnel to anchor users in the company's ecosystem (think of Surface, Windows, and Office).
</p>

So how can we apply these insights to the world of quantum computing? Specifically, should we expect the companies building quantum hardware to have an inherent advantage in building the software for those devices, or is it possible that companies focused solely on software and applications will be able to achieve dominance?

## Quantum computers are specialized devices

Here, I think it's worth pointing out a key difference between traditional (classical) computers and quantum computers: **Quantum computers are unlikely to ever be used as general-purpose computing devices -- at least for the next several decades.** Yes, in theory, a quantum processor can do anything a classical processor can do, but our classical computing technology is so fast, so small, so cheap, and so satisfactory for most purposes, that it will require many orders of magnitude of advances in quantum technology to begin to even consider replacing classical computers in the broad sense. So, for now, we can think of quantum computers as special-purpose devices that are optimized for a few particular tasks -- essentially, as "co-processors" whose operation will be controlled by a classical computing framework. This certainly describes the current area of research into near-term ["hybrid quantum-classical" systems](https://www.epiqc.cs.uchicago.edu/hybrid-quantum-classical-computing), but it will continue to be true even after quantum computers reach the stage of fault-tolerance and universality.

With this in mind, it's relatively easy to see that the companies building quantum hardware should also be building the core software for these devices, since the scenario falls neatly into cases (a) and (b) in the framework laid out above. The two are necessarily intertwined, and it's impossible for someone else to effectively build the core software -- especially in a world where companies don't even sell the quantum computing hardware itself, but only sell access to it over the cloud.

## The future rise of quantum software and applications

So is that the end of the story? Should all of the quantum software companies cease to exist? Of course not! The quantum computing hardware companies must build the core software, but this software is more analogous to a device driver -- it provides access to the underlying hardware, but it doesn't necessarily provide value on its own. It takes applications to do this. In fact, I would argue that in the most likely scenario, quantum software and applications companies will extract most of the value from the quantum computing market in the long-term -- that is, I would argue that quantum software will indeed "eat" the quantum industry. Reasons for this include:

**Quantum computers will eventually become a commodity.** Once quantum hardware has reached the stage of fault-tolerance, device-specific attributes become much less important. More and more companies will begin building universal quantum computers whose capabilities are all roughly equivalent. At this point, it helps to recall the history of the personal computer: IBM enjoyed enormous success initially, but as more and more companies began producing systems with equivalent capabilities, the unique value of the IBM PC began to disappear. This dynamic allowed a software company, Microsoft, to rise and become one of the dominant beneficiaries of the explosion of the PC industry.

**Most applications for quantum computers have not been discovered yet.** If we already knew everything a quantum computer could do, then the companies building the quantum computers could also build the applications, and everything would be done. But this certainly is not the case. In fact, most quantum computing companies today are focused on near-term algorithms and applications, and it's not even clear yet whether there is anything useful that these near-term quantum computers can do. It's far more likely that the most relevant applications will emerge later, once the hardware has matured and we have fault-tolerant devices. At that point, since the hardware will have already begun to commoditize, the companies discovering and developing these applications will likely be able to provide the most value to the marketplace.
