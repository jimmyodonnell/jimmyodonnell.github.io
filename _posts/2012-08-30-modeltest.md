---
layout: post
title: Cooking Up a Fresh Batch of ModelTest
excerpt:
tags: [phylogenetics, science]
comments: false
---

jModelTest is an easy-to-operate program that allows users to calculate the likelihood that a block of DNA sequences (alignment) is the result of sequence evolution under each of up to 88 substitution models (many more variants in jModelTest2). There are lots of reasons you might want to run batches of alignments through jModelTest: For instance, you are interested in evaluating whether different alignment methods affect model inference, or you are working with multiple genes and want to run one alignment after another. The alignments I am working with right now take about 1.5 to 2 hours to run on my computer (2.4GHz Dual Core MacBook Jr), and it's a pain to keep reloading alignments rather than just loading a batch before bed. However, I couldn't find any straightforward explanation of how to run batches of alignments through jModelTest. I'm no computer whiz, so what follows is my surely inelegant solution.

First, you will need to install [jModelTest2](https://github.com/ddarriba/jmodeltest2), which, in addition to the Java GUI, can be run from the command line in terminal. I would put the alignments (as nexus files with the extension .nex) in the same folder as the program ("jmodeltest-2.1.1" folder by default), either all together or in their own folder. Then, write out in a text editor the commands to execute the program according to your specifications. All you need to do is tell your computer to run jModelTest2, which file to use, the models you'd like to evaluate, and how you'd like to evaluate them.

A pretty standard run would look like this:

`$ java -jar jModelTest.jar -d myfile.nex -s 11 -g 4 -i -f -S NNI -t ML -AIC -BIC`

Where from java to .jar executes the program, and everything that follows are the details/settings ("arguments"). In order, we've told jModelTest to use "myfile.nex", evaluate 11 substitution schemes, include models with rate variation among sites for 4 categories, include models with invariable sites, include models with unequal base frequencies, use the Nearest Neighbor Interchange algorithm to search tree topologies, use a maximum likelihood tree as the base tree, and then evaluate the likelihoods of all of these using Akaike's Information Criterion and Bayesian Information Criterion.

Then, all you have to do is copy that code as many times as you have files to run, paste in your file names, and glue them all together on one line separated only by a space, semicolon, and another space. Pour yourself a scotch or bourbon, hit the hay, and wake up in the morning to your terminal console filled with your results, ready to save to text files.
