# Inferring Species Trees

This repository contains tutorials for learning about inference of species trees from gene trees that vary according to some process (such as coalescent sorting, horizontal transfer, or gene duplication and loss). We will use [RevBayes](https://revbayes.github.io) to do inference under the full multispecies coalescent model. We will also use ASTRAL to perform fast species tree analyses that are scalable to large datasets, but also come with some tradeoffs. You will need [RevBayes](https://revbayes.github.io) and [ASTRAL](https://github.com/smirarab/ASTRAL#installation) available on your machine, along with [FigTree](http://tree.bio.ed.ac.uk/software/figtree/) or another tree viewer.

- [Simulate gene trees under the multispecies coalescent](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/Simulate_gene_trees.md)

- [Carry out a multispecies coalescent analysis in RevBayes](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/RB_MultispeciesCoalescentTutorial.md)

Now we'll carry out fast species tree analyses with ASTRAL. We can start by re-analyzing the same data that we just analyzed in RevBayes. To do so, download [this](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/unrooted_trees.tre) file which simply contains unrooted estimates of gene trees for the loci that we just analyzed in RevBayes. You can run a quick ASTRAL analysis of these gene trees with:

```
java -jar astral.5.6.3.jar -i /path/to/unrooted_trees.tre -o species.tre
```
Open this estimate of the species tree with FigTree and compare it to your estimate from RevBayes. Are the trees similar? What is likely driving any differences?

ASTRAL contains much more functionality and easily scales to thousands of gene trees. The following turtorial will explain much of this extra functionality and provide examples of very large scale analyses.

- [Carry out fast species tree analysis with ASTRAL](https://github.com/smirarab/ASTRAL/blob/master/astral-tutorial.md)

We'll use two additional pieces of software to perform species tree inference under the multispecies network coalescent and gene duplication and loss. You'll need [PhyloNet](https://bioinfocs.rice.edu/phylonet) and [PHYLDOG](https://pbil.univ-lyon1.fr/software/phyldog/) to work through the respective tutorials.

- [Inference under the Multispecies Network Coalescent with PhyloNet](https://wiki.rice.edu/confluence/pages/viewpage.action?pageId=8898533#PhyloNetTutorial%28SpeciesPhylogenyInference%29-5.VisualizingaPhylogeneticNetwork)

- [Joint inference of species trees and gene duplication and loss histories with PHYLDOG](https://pbil.univ-lyon1.fr/redmine/projects/phyldogtoolt/wiki/Tutorial)
