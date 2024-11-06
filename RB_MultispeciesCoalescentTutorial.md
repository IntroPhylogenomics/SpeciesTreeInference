# Joint inference of species and gene trees

The tutorial and data files below will walk you through an analysis to jointly infer gene trees and species trees. 

- [Tutorial](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/RB_MultispeciesCoalescent_Tutorial.pdf)
- [Data and scripts](https://github.com/IntroPhylogenomics/SpeciesTreeInference/blob/master/RB_MultispeciesCoalescent_Tutorial.zip) (Download this 6MB zip file)

There are some minor differences between the code copied in the pdf and the rev scripts supplied with the tutorial, that relate to changes in how MCMC moves are set up and used in RevBayes. The scripts should all run properly in RevBayes 1.2.4, but youʻll see some difference if you are copying code from the pdf. The zip file also contains a bash script that will carry out gene tree inference for each gene on its own. This can take a long time, so the tutorial also provides pre-computed gene trees. After your species tree analysis finishes, compare these gene trees to your species tree. Where do the topologies differ? What might this tell you about population demographics along this branch of the tree.
