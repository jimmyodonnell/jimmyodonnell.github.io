---
layout: post
title: Puzzling BEAST error
excerpt: 
date: 2014-04-02
tags: [phylogenetics]
comments: false
---
If one were to trace back in time the sequence of a given stretch of DNA, that gene’s history wouldn’t necessarily perfectly represent the history of the lineages of individuals harboring it. Thus, if you want to know the true history of lineages of individuals, you should compare the lineages of multiple genes. One can accomplish this using the software package [BEAST](http://beast2.org/), using the atrociously named extension *BEAST (pronounced “star beast”). Until you can pronounce words into search engines, cleverly named programs like this will be a pain in the neck for users.

BEAST comes with a separate program, BEAUti, to generate the XML file it uses as input. After loading my alignments into BEAUti with no apparent problems, specifying a bunch of parameters, and exporting the XML file, I got this error when trying to run the analysis in BEAST:

```
java.lang.Exception: Could not find a proper state to initialise. Perhaps try another seed.
```

Amply vague, but after much gnashing of teeth, searching of documentation, and reinstalling unstable versions, I discovered that my alignments were the problem.

*BEAST requires a species be represented by at least one sequence in the alignment of every locus, whether you have data or not.* That is, if you have sequence data for 10 species for 20 loci, but are missing data for one species at one locus, you MUST include a dummy sequence for that species in the alignment of that locus. I think one part of my confusion somehow came from the fact that it does not matter to BEAST whether sequence data across loci comes from the same individual. So a sequence named similarly to other alignments but filled with N or ? will suffice.

Note also that the estimation of a species tree using a coalescent approach (as performed by BEAST) is premised on the fact that each species is represented by multiple individuals for multiple genes. Missing data should be problematic, though it is not clear to what degree, particularly with empirical data. Remember that the other side of the “missing” data coin is that additional but incomplete data may strengthen an analysis. In the case above, 19 loci for 10 species may not perform as robustly as 20 loci, even if the additional locus has not been sampled from one species. I always like to look on the bright side of things.

To be absolutely certain there’s no confusion: *When using *BEAST, EACH NEXUS FILE NEEDS TO HAVE AT LEAST ONE REPRESENTATIVE FROM EACH SPECIES*.