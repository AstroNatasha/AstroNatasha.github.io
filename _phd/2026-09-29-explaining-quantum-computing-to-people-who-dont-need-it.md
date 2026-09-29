---
layout: phd_post
title: Explaining quantum computing to people who don't need it
date: 2026-09-29
---
I once had to explain my research to a mixed audience. Some of the people in the room wrote software for a living. Others had never needed to think about how a computer works, and had no particular reason to start. The explanation most of us reach for in that situation says that a quantum bit can be 0 and 1 at the same time, so a quantum computer can try every answer at once. I think that explanation is wrong in a way that matters.

Here is the problem with it. Suppose a machine really did try every possible answer at once. At the end you still have to look at it, and when you look at a quantum computer you get one result, chosen at random. A machine that explores every answer and then hands you a random one is no better than guessing. Whatever quantum computers are good for, it cannot be that.

The better explanation needs one idea that has no everyday equivalent, and it is worth taking slowly.

![quantum-computers-and-accelerated-discovery_40645906341_o-1000](/images/misc/quantum-computers-and-accelerated-discovery_40645906341_o-1000.jpg)

Start with a coin. If I flip a fair coin, there is a 50% chance of heads. If I flip it again, the chance is still 50%. Randomness piles up and never undoes itself. That is because probabilities are always positive numbers, and when there are several ways to reach the same outcome, their probabilities add.

A qubit is described differently. Instead of a probability for each outcome, it carries a number called an amplitude, and the probability you observe comes from squaring it. The crucial difference is that amplitudes can be negative. (Strictly speaking they can be complex numbers, but negative ones are enough to see what matters.) When two ways of reaching the same outcome have amplitudes of opposite sign, they do not add up. They cancel.

This produces something a coin cannot do. There is a simple operation that takes a qubit in state 0 and leaves it in an even mix, where measuring would give 0 or 1 with equal odds. So far this looks exactly like flipping a coin. But apply the same operation a second time and the qubit comes back to 0, every time. There were two routes to the outcome 1, one with a positive amplitude and one with a negative amplitude, and they erased each other. The two routes to 0 had the same sign and reinforced each other. A coin flipped twice is still random. A qubit "flipped" twice can be certain again.

That is interference, and it is the real engine of quantum computing. Waves do something similar. Two ripples in a pond can meet crest to trough and flatten the water, which is also the principle behind noise-cancelling headphones. A quantum computation is a carefully arranged pattern of interference, designed so that the routes leading to wrong answers cancel and the routes leading to the right answer reinforce. When you finally measure, the randomness is still there, but it has been tilted heavily toward what you wanted.

This is where the "every answer at once" story holds a grain of truth. Describing n qubits takes 2ⁿ amplitudes, so fifty qubits involve about a million billion numbers, far more than an ordinary computer can comfortably track. But you never get to read those numbers out. You only get to shape them through interference and then take one sample.

Seen this way, the limits of quantum computing stop looking mysterious. Arranging the cancellations requires the problem to have some structure the interference can grab onto. Factoring large numbers has it, because it can be turned into the problem of finding a repeating pattern, and waves are very good at detecting repetition. That is why Peter Shor's 1994 algorithm factors numbers dramatically faster than the best known classical method. Searching an unstructured list has only a little of that structure, so the gain there is modest, a square-root improvement. For many other problems nobody has found a useful pattern of cancellation at all. And more than once, after researchers announced a quantum speedup, someone found a classical algorithm that did about as well.

There is also a physical catch. Interference only works while the qubits are left undisturbed. Heat, vibration or a slightly imperfect control pulse scrambles the amplitudes, and the careful cancellations fall apart. This is why today's machines are small and noisy, and why current estimates for a quantum computer able to break modern encryption run to hundreds of thousands or even a million physical qubits, most of them spent correcting errors rather than computing.

So this is what I would want anyone in that room to leave with. A quantum computer is not a faster computer. It is a different kind of computer that does one strange thing, making possibilities cancel, and that strange thing turns out to be very powerful for a small set of problems. The open question is which problems belong to that set. Much of my own work in quantum computing is spent checking whether a well-tuned classical method does just as well, and often it does. That is not a disappointment. It is how we find out where the real boundary is.

Nobody in that audience needed any of this to do their job. But I think it is worth knowing that behind the headlines there is one idea, strange and simple at the same time, and that it can be understood without a physics degree (or any).
