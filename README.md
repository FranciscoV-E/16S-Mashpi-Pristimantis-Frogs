# 16S phylogeny for Mashpi-Tayra *Pristimantis* Jiménez de la Espada,1870
The conservation of the Andean Cloud forests of Ecuador depends, to a large extent, on the documentation of biodiversity. Despite the impressive number of anurans described during the last decade, some places, such as the canopy, remain unexplored. This forest layer possesses unique qualities in terms of composition. For example, epiphytes, despite being used by a vast variety of organisms (e.g.: bromeliads) very few studies focus on them.  To study the canopy, it is necessary to implement specific arborist techniques, which allow climbing and moving to access the bromeliads. Once we reach the canopy layer, we sample all the anurans inside the bromeliads. Tissue was collected for posterior sequencing of the mtDNA 16S rRNA segment for phylogenetic taxonomical identification. With the new sequences and all the available sequences of the same DNA fragment (16S) from frogs of the genus Pristimantis Jiménez de la Espada, 1870, we build a new phylogenetic hypothesis for the relationship between the canopy and terrestrial individuals of the genus Pristimantis inside the Mashpi-Tayra reserve, to answer the question: Are inside the anurans found in the canopy layer potential new species? After the generation of a new phylogenetic tree, we can expect that at least one of the two different morphospecies registered in the canopy belongs to a new species. The documentation of new species could be directly used in conserving Andean cloud forests, especially in the face of deforestation.

First up, download the data.

```bash
# download data
mkdir 16sfrog
cd 16sfrog
# Download from the following collections
# Pristimantis recorded in Mashpi-tayra https://www.ncbi.nlm.nih.gov/sites/myncbi/francisco.velasquez.2/collections/63500314/public/ 
# Outgroup https://www.ncbi.nlm.nih.gov/sites/myncbi/francisco.velasquez.2/collections/63510721/public/
# The remaining sequences (generated for the new registers) will be available in GenBank once they are published  
cd ..
```

Next, install the following programs via conda. (Fresh environment suggested).

```bash
conda install -c bioconda mafft
conda install -c bioconda iqtree
```

### Aligning the sequences and making the tree  

We'll use mafft with the following settings for the multiple sequence alignment.  
mafft-qinsi --maxiterate 2 --thread 4 --threadtb 5 --threadit 0 --reorder input > output

### Aligning the sequences and making the tree  

#IQTREEPATH -s #DATASETPATH -m #MODEL -bb #NUMBEROFBOOTSTRAP 
(you may have an error once this line of code is run. This happens because we are rewriting in the same folder. Thus, we need to implement the command -redo)

### Viewing the tree  

*Viewing it in FigTree*
Download it from here http://tree.bio.ed.ac.uk/software/figtree/ (friendly user 😎)

*Viewing it on R*
IQtree produces a "contree", you can Cat this file onto the screen, and copy everything      
In R, write this:

    library(ape)
    library(ggtree)
    shh_tree <- "" # BUT PASTE IN YOUR CONTREE WITHIN THE QUOTES
    shh_tree <- read.tree(text=shh_tree)
    # Rerooting
    shh_tree <- ape::root.phylo(shh_tree, outgroup = "OUTGROUP NAME")
    ggtree(shh_tree) + geom_tiplab() 

### Final product 
![image](https://github.com/FranciscoV-E/16S-Mashpi-Pristimantis-Frogs/assets/57726892/6f9f1bd2-48e6-42aa-888b-ef9d0a934c98)

    

