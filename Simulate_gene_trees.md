# Simulating gene trees under the multispecies coalescent

This file will walk you through simulating gene trees under the multispecies coalescent given a species tree and population sizes.

First, create a folder to store our simulations in. To do so, open terminal and type:

```
mkdir simulatedTrees
```
Now we start RevBayes by typing:

```
rb
```
First, we'll tell Revbayes to save our simulations in the folder we just set up:

```
dataFolder = "simulatedTrees/"
```


We'll simulate a species tree with 5 species, and then simulate 10 gene trees that sample 2 alleles for each species:

```
n_species <- 5
n_genes <- 10
n_alleles <- 2
```
We can use a for loop to easily set up species names:

```
for (i in 1:n_species) {
        species[i] <- taxon(taxonName="Species_"+i, speciesName="Species_"+i)
}
```

Now we can simulate the species tree under a model for species trees called the Birth Death process, and save this tree to a file. Here lambda is the rate at which speciation happens, mu is the rate at which extinction happens (we set this to zero, so we assume extinction does not happen), and rootAge is the total age of the tree that we will simulate. Rho refers to the fraction of species in the tree that we have sampled (we will assume they are sampled, so this fraction is set to 1.0).

```
spTree ~ dnBirthDeath(lambda=0.3, mu=0, rootAge=10, rho=1, samplingStrategy="uniform", condition="nTaxa", taxa=species)
write(spTree, filename=dataFolder+"speciesTree.tre")

```
Open this file in FigTree (or another tree viewer) to see our simulated topology. Before we can simulate gene trees under this species tree, we need to specify the population sizes along its branches. Here, we'll simply assume that all branches have the same population size (arbitrarily set to 30).

```
popSize <- 30
```
> __Questions__
>
> (1) What should happen to the rate of incomplete coalescence in our gene trees if we increase the population size by (say) an order of magnitude?
>
> (2) What should happen if we change the age of the tree?

Now we can simulate our gene trees and write them to file:

```
for (g in 1:n_genes) {
  for (i in 1:n_species) {
    for (j in 1:n_alleles) {
        taxa[g][(i-1)*n_alleles+j] <- taxon(taxonName="Species_"+i+"_"+j, speciesName="Species_"+i)
    }
  }
  geneTrees[g] ~ dnMultiSpeciesCoalescent(speciesTree=spTree, Ne=popSize, taxa=taxa[g])
}
write(geneTrees, filename=dataFolder+"geneTrees.tre")
```
Now we can go to our save folder and open the gene trees in FigTree (use the arrows at the top of the window to go through them).

> __Questions__
>
> (1) How often do we see non-monophyletic species across the gene trees? Should this go up or down if we make the population size smaller?
>
> (2) How many gene trees have topologies that match the species tree? Again, should this go up or down if we make the population size smaller?

> __Practice__
>
> (1) Modify your script in order to test this prediction by redoing the simulation with a population size of 3. Be sure to modify your file names to avoid overwriting results.

