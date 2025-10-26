---
title: "Should We Trust Quantum Computers?"
date: 2020-03-10T17:44:00-05:00
categories:
  - Blog
tags:
  - quantum computing
---

Imagine the following scenario. You are responsible for the safety of a large chemical plant. By some unfortunate administrative oversight, your plant's entire supplies of Xotheasium, Yucruinium, and Zatreilium have been put on conveyor belts and are moving toward an enormous vat. The Xotheasium and Yucruinium will both reach the vat 15 minutes from now, and the Zatreilium will reach the vat 20 minutes from now. It is well-known, of course, that Xotheasium and Zatreilium react explosively, and if they come in contact, your plant will explode and anyone inside will surely die. And as luck would have it, the control system for the conveyor belt is currently restarting due to a Windows Update and will not be usable for the next 15 minutes.

<img src="/images/xyz-chemicals.png" alt="Illustration of chemicals on conveyor belts" width="550" />

You would have enough time to stop the Zatreilium, but the big problem is the Xotheasium and Yucruinium. As far as anyone knows, these exotic chemicals have never been in contact with each other, and their chemical properties are far too complex to simulate on any computer. But Yucruinium shares many traits with Zatreilium, and so experts predict that there is a 50% chance that the reaction would be explosive, which would destroy your plant and everyone inside. But there is also a 50% chance that Yucruinium is inert and that there would be no reaction.

So as the safety manager, you command that everyone else immediately evacuate the plant, which they do. But you yourself are torn between two options:  
**(1) Evacuate.** It's a large plant, and it takes 10 minutes to get in or out. This means that no one will be around to stop the conveyor belt when the Windows Update finally finishes, and in either 15 or 20 minutes your plant will surely explode and your company will be forced into bankruptcy.  
**(2) Wait.** Hope that Yucruinium is inert. If so, you'll be able to stop the conveyor belt and save the plant and the company. If not, you die.

Your self-preservation instincts kick in and you decide to evacuate. But just then, you get a notification on your phone. A paper has just been posted to the arXiv which claims to show that Yucruinium is, in fact, inert. The calculations were done on the world's first and only fault-tolerant quantum computer. You trust that the authors have reported their results correctly. So the question is: **Do you trust the results of the quantum computer?**

## Verifying a powerful device

Ridiculous life-or-death chemical plant scenarios aside, the issue of how to verify the answer to a problem you can't solve yourself is a well-studied one in computer science. For some problems it's easy. Consider factorization of the product of two very large prime numbers: if the numbers are large enough, this is impossible to solve with today's computers; but if someone tells you one of the factors, you can easily verify whether it is a correct answer by simply performing the division.

Unfortunately, for some problems it's not easy at all. Think about the so-called "traveling salesman problem" (TSP), where you must find the shortest route that travels through a set of, say, 50 cities. Good heuristics exist to find approximate solutions to this problem, but an exact solution is infeasible -- consider the fact that there are 50! (factorial) possible routes. But even if someone gives you a route from their magic-TSP-solver and claims that it's the shortest, how can you verify this? To have complete confidence, you'd still have to solve the problem yourself. And we've already said that can't be done.

The first time I became aware of this problem, I thought surely it was impossible. What approach could you possibly use to verify answers from some super-powerful device that solves "unsolvable" problems?

Then I saw a [**talk by Anne Broadbent**](https://www.youtube.com/watch?v=X1hSuqpLcA8) with a very enlightening illustration (starting at 8:40 of the video), which I will loosely paraphrase here. Imagine you have an app on your phone which promises to exactly count the number of leaves on any given tree. You go to the largest tree in the world and open the app. It tells you the tree has exactly 893,145 leaves.

How do you know whether you can trust this app? (No, you can't climb the tree and count the leaves yourself. And even if you could, I doubt you'd have much confidence in your own result after you finished counting.)

You can simply walk up to the tree (turn off your phone first, if you're paranoid) and pick off 18 leaves (or any number you choose). Then, open the app again and see what it says. If it's not exactly 893,127 (which is 893,145 - 18), then you know it can't be trusted. (Ok, yes, I'm assuming no leaves were blown away by the wind.)

But what if it does give you the right answer? It still doesn't prove anything; it could have been a lucky guess. Let's be generous and say there was a 1% chance it could have guessed correctly. So you now have 99% confidence that the app is counting the leaves correctly. What if that's not good enough? Just repeat the leaf-removal process. If it gives you the correct answer again, you now have 99.99% confidence. And so on. You can do this as many times as you want to increase your confidence as much as you would like.

The simplicity and elegance of this approach is remarkable. And what's even more amazing is that it bears so much resemblance to the approach that is used for verifying the results of quantum computations. (This is all in theory, of course. No one has a quantum computer yet whose results are actually good enough to be verifiable -- more on that later.)

Verification of quantum computations has been studied for a number of years, and the final pieces of the puzzle were recently put together by Urmila Mahadev ([**video**](https://www.youtube.com/watch?v=RQGW4KcLMIQ) and [**paper**](https://arxiv.org/abs/1804.01082)). She proved (with reasonable assumptions) that it is actually possible for a classical device -- i.e., a non-quantum computer -- to ask a very specific series of questions to a quantum computer that can prove, with a particular degree of confidence, that a given quantum computation was performed correctly. And the degree of confidence can be increased by simply asking more of these questions. The trick, very loosely speaking, is for the classical device to encode some "secret" in the desired computation in a way that the quantum computer is unable to detect, and then to ask questions which can prove (with some probability) whether that secret was faithfully maintained throughout the computation. It's exactly like the tree and the leaves -- you gain an advantage over the leaf-counting app by keeping the "secret" of how many leaves you removed, and you can use this to verify that the app is operating correctly.

## What about noisy, error-prone devices?

So, this is all great if we have a quantum computer that gives us exactly-correct answers. But, in fact, such devices (often called "error-corrected" or "fault-tolerant" quantum computers) don't exist right now, and likely won't exist for quite a few years. The quantum computers we have now are noisy and error-prone, which means they can only give approximate answers. And the scheme we discussed doesn't work very well if we know that the quantum computer always makes errors and never gives an exactly-correct answer.

Near-term quantum computers are often referred to as NISQ (noisy intermediate-scale quantum) devices, and the strategy for testing the performance of these devices often centers around _benchmarking_ a device's performance, rather than outright verification of results. Benchmarking is a process in which the lowest-level operations of the device -- the building blocks underlying any algorithm or computation -- are thoroughly tested and characterized. Typically this produces a number for each low-level operation (i.e., "gate"), called the "fidelity", that indicates how closely the operation matches the ideal behavior. For current devices, this number is often something like 99% or 99.9% per operation -- but this varies widely depending on the hardware being used and the operation being performed. These numbers seem great, but since most useful quantum algorithms require thousands or millions of operations (or more!), the errors quickly accumulate to the point where these applications are out of reach for now. This is why researchers are focused so heavily on developing an error-corrected device. Not only will this eventually allow us to implement large-scale quantum algorithms, such as Shor's integer factorization algorithm, but it will also enable the secret-based verification strategies we discussed earlier.

Now, a short aside for a topic of personal interest (this is my blog, after all). There's a possible near-term application of quantum devices known as "analog quantum simulation". This concept actually existed before the modern ideas of gate-based quantum computing. The idea is to take some system from nature that is too hard to simulate on our existing computers, say a very complex molecule of some kind, and develop a quantum computing device that "emulates" or "simulates" the behavior of that natural system, so that we can learn more about it. These devices are also error-prone, meaning that exact verification schemes are unlikely to be helpful, but we should be able to benchmark the performance of these devices in much the same way that we benchmark gate-based quantum computers. My group recently posted a **[paper](https://arxiv.org/abs/2003.04500)** demonstrating a few possible strategies. The overarching idea (which is the same as for gate-based benchmarking) is to make the device perform complicated sequences of operations which are specially designed such that, if the system is perfect and error-free, the quantum system will be left unchanged. And so by running these sequences on your actual device and measuring how much the state changes, you can gain some sense of how error-prone or noisy your device is.

## Learning more

If you want to learn a little more about the fascinating topic of verifying quantum computations, I highly encourage you to watch one or both of these talks (which were also linked above):

**"How to Verify a Quantum Computation"** by Anne Broadbent  
Video: <https://www.youtube.com/watch?v=X1hSuqpLcA8>  
Paper: <https://arxiv.org/abs/1509.09180>

**"Classical Verification of Quantum Computations"** by Urmila Mahadev  
Video: <https://www.youtube.com/watch?v=RQGW4KcLMIQ>  
Paper: <https://arxiv.org/abs/1804.01082>

(By the way, you came to your senses and quickly evacuated the chemical plant. That paper hadn't even been peer-reviewed yet. And miraculously, while you were on your way out, the Windows Update terminated with a blue screen of death, causing the system to restart into Safe Mode, which triggered a bug in the control software that suddenly stopped all the conveyor belts. The plant is saved! But alas, the inertness of Yucruinium will have to be decided by the Nature referees.)