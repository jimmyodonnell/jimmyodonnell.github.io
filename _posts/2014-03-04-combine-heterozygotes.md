---
layout: post
title: Combine heterozygous DNA sequences in R
excerpt: 
date: 2014-03-04
tags: [R, genetics]
comments: false
---
Most folks know  the nucleotides that make up strands of DNA are represented by letters (A, G, C, T). But if you’re unsure of the nucleotide at a given spot, it can be represented by another letter that conveys your level of uncertainty. For example, “I know there’s a nucleotide here, but I have no idea what it is” is represented by an N. “This is either adenine or guanine (A or G)” can be represented by an R.

Like humans, most of the organisms we work with have DNA in the nucleus of their cells that comes in two copies, but in some places the sequences may not be identical. For example, if the strand inherited from your mom is ATG and the strand from your dad is ATA. In that case, if we want to use a single sequence in our analysis, we would code that piece as ATR.

I’ve run into this in with my own work on small scales, but a lab mate was having this issue with his data (restriction site associated DNA sequences generated from last-gen sequencing aka massively parallel sequencing on an Illumina machine). We didn’t try very hard, but couldn’t quickly find any functions already written in R or Python, so I wrote one that would do this for any pair of sequences of equal length. Note that because there are a large number of possible file types for storing DNA sequences (the number is proportional to the number of scientists who think they should reinvent the wheel in order to get more citations), I didn’t generalize it in any way. Thus, it’s up to you to get your sequences into R, and then use this function paired with one of the apply functions to find and consolidate the heterozygous sequences. You can find the code [here](https://gist.github.com/jimmyodonnell/9355907).
