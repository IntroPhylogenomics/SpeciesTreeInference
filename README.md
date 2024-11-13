# Inferring Species Trees

This repository contains tutorials for learning about inference of species trees from gene trees that vary according to some process (such as coalescent sorting, horizontal transfer, or gene duplication and loss). We will use [RevBayes](https://revbayes.github.io) to do inference under the full multispecies coalescent model. We will also use ASTRAL to perform fast species tree analyses that are scalable to large datasets, but also come with some tradeoffs. You will need [RevBayes](https://revbayes.github.io) and [ASTRAL](https://github.com/chaoszhang/ASTER) available on your machine, along with [FigTree](http://tree.bio.ed.ac.uk/software/figtree/) or another tree viewer.

- [Simulate gene trees under the multispecies coalescent](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/Simulate_gene_trees.md)

- [Carry out a multispecies coalescent analysis in RevBayes](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/RB_MultispeciesCoalescentTutorial.md)

Now we'll carry out fast species tree analyses with [ASTRAL](https://github.com/chaoszhang/ASTER). We can start by re-analyzing the same data that we just analyzed in RevBayes. To do so, download [this](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/unrooted_trees.tre) file which simply contains unrooted estimates of gene trees for the loci that we just analyzed in RevBayes. You can run a quick ASTRAL analysis of these gene trees with:

```
astral4 -i /path/to/unrooted_trees.tre -o species.tre
```
Open this estimate of the species tree with FigTree and compare it to your estimate from RevBayes. Are the trees similar? What is likely driving any differences?

ASTRAL and related programs contain much more functionality and can scale to thousands of gene trees, whole genome alignments, and multi-copy gene families. The following documentation will explain much of this extra functionality and provide examples of very large scale analyses.

- [Accurate Species Tree EstimatoR ASTER**](https://github.com/chaoszhang/ASTER/tree/master)

You might also be interested in [SVDQuartets](https://www.asc.ohio-state.edu/kubatko.2/software/SVDquartets/), which provides another way to estimate species trees using quartets. This approach estimates quartets directly from the distribution of site patterns in the data, and so relies less on assumptions about gene trees being estimated correctly.

Multiple software packages are also available that allow for species tree estimation when reticulation has occurred. Two widely used options include:

[PhyloNet](https://phylogenomics.rice.edu/html/phylonetOverview.html) which provides several different ways of estimating phylogenetic networks from both sequence and SNP data.

[PhyloNetworks](https://github.com/JuliaPhylo/PhyloNetworks.jl?tab=readme-ov-file) which provides methods for estimating phylogenetic networks using quartets, as well as several tools for working with, plotting, and carrying out comaprative analysis with these networks.

Finally, duplication and loss within gene families can also lead to variation among gene trees. Available tools for estimating phylogeny in this scenario include:

[ASTRAL-PRO](https://github.com/chaoszhang/ASTER/blob/master/tutorial/astral-pro3.md) which uses quartet scores to infer phylogeny similar to ASTRAL, but accounts for duplication and loss within gene families.

[GeneRax](https://github.com/BenoitMorel/GeneRax) which performs maximum likelihood estimation of gene family histories, including duplication and loss, as well as species trees.
