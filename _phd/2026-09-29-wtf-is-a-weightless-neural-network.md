---
layout: phd_post
title: WTF is a Weightless Neural Network?
date: 2026-09-29
---
Ok, so... This September I presented a poster on QUBO-WiSARD at CBCTQ, the Brazilian Congress of Quantum Sciences and Technologies, in Niterói. I expected the difficult conversations to be about the quantum side of the work. They were not. Most of the people who stopped at my poster knew neural networks well, and almost every conversation stalled at the same point, long before we reached any optimization. I would say that the model has no weights and no backpropagation, and I could see the explanation stop working right there. I tried different versions of it throughout the session and none of them really landed. At some point I realized the problem was mine. I had spent so long with these models that I had forgotten which parts seem strange to someone who learned machine learning through gradients. This post is my second attempt.

Most of us learned that a neural network is a set of weights and that learning means adjusting them. You compute a loss, take its gradient, nudge every weight a little and repeat for many epochs. From there, "weightless neural network" sounds almost like a contradiction. **If there are no weights and no backpropagation, what exactly is being learned?**

The short answer is that learning becomes writing to memory. The longer answer is worth walking through, because once it clicks the idea fits in a paragraph, and it says something interesting about what learning actually requires.

The best-known model in this family is WiSARD, named after Wilkie, Stonham and Aleksander, who built it as a hardware recognition device in the early 1980s. Its roots go back further, to the n-tuple method that Bledsoe and Browning proposed in 1959 for machine reading of characters.

Take a familiar task, recognizing handwritten digits in 28 by 28 pixel images, and suppose for now that each pixel is either black or white. That gives 784 bits per image. WiSARD starts by shuffling those bits into a fixed random order and cutting them into groups of, say, eight. That leaves 98 groups, and each group is wired to its own small memory, called a RAM node. The eight bits a node sees act as an address. Eight bits can form 256 patterns, so each RAM has 256 cells, all starting at zero.

Each class, here each digit, gets its own set of these 98 RAMs, called a discriminator. All discriminators share the same random wiring.

Training is almost nothing. Show the network an image of a 3. Each of the 98 RAMs in the "3" discriminator reads its eight pixels, forms an address and writes a 1 into that cell. That is the entire update. There is no loss, no gradient and no second epoch. The next image of a 3 writes its own 98 ones, some of which land on cells that were already set.

At inference, a new image goes to all ten discriminators at once. Each RAM reads its eight pixels and returns whatever is stored at that address, a 1 if this local pattern appeared in training for that class and a 0 if it did not. Each discriminator adds up its answers into a score between 0 and 98, and the highest score wins.

The obvious objection is that this is memorization, and it is. What makes it generalize is that nothing memorizes the whole image. Each RAM remembers only a fragment of eight pixels. A new 3 will differ from every training example somewhere, but most of its fragments will still look like fragments of 3s the network has already seen. It might hit 85 of the 98 RAMs in the "3" discriminator and only 40 in the "7" discriminator. No single fragment has to match. The vote does the work.

Seen from the side of conventional networks, the word "weightless" is a little misleading. The network does have parameters. They are the contents of the memory cells, about a quarter of a million bits in this example. They are binary instead of continuous, and they are set by a direct write instead of by following a gradient. Each RAM node can represent any Boolean function of its eight inputs, which a single artificial neuron cannot do. What WiSARD gives up is the ability to learn which inputs belong together. The grouping of pixels is fixed at random before training begins, and learning only fills in the tables.

That design has consequences in both directions.

The good ones come from the training rule. Learning takes a single pass, every example touches a fixed number of cells, and adding new examples or even a new class later never erases anything already written. Inference is a series of memory lookups followed by a sum, which is why this family of models has long been attractive for low-power and custom hardware.

The bad ones come from the same simplicity. The first is the size of the groups. With small groups, each RAM has few cells and many images write to the same ones, so the network generalizes easily but soon every discriminator answers yes to almost everything. With large groups, the tables are huge and sparse, and the network recognizes only what looks very close to its training data. Group size is the main knob trading generalization against memorization, and it plays roughly the role that capacity plays in a conventional network.

The second problem is saturation. With enough data, most cells in every discriminator end up set to 1 and the scores stop telling classes apart. A common fix, called bleaching, stores counts instead of single bits and raises a threshold on those counts until one class clearly stands out.

The third is that the input must be binary. Grayscale pixels, sensor readings and any continuous feature first have to be turned into bits, usually with a thermometer code in which a larger value switches on more bits. How much information that encoding keeps often matters as much as the network itself.

And on hard perception problems a WiSARD does not come close to a well-trained deep network. It has no layers building features on top of features, and its only structural decision, how the input bits are grouped, is left to chance.

That last point is the one I find most interesting. If the random grouping is the only structure the model has, then a lot of its performance is decided there, and choosing that grouping well is a discrete optimization problem, not a gradient problem. That question is a large part of what I work on, and it deserves its own post.

For now, the central idea is enough. A neural network does not need weights to learn. It needs a way to store what it has seen and a way for many partial memories to vote on what it is seeing now. Gradient descent is one very successful way of doing that. A table of bits is another.
