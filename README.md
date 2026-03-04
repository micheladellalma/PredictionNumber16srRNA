# PredictionNumber16srRNA
The aim is the prediction of the number of 16s rRNA gene copies in bacterial genomes, using comparative phylogenetics methods.
The analysis focuses on bacteria belonging to the class Alphaproteobacteria and uses available genomes to infer the number of 16S rRNA copies in new genomes.

## How to use

**Input required**: 
a table containing two columns:
- accession numbers
- organisms' names

**Output**:
Prediction of the number of 16S rRNA copies for new genomes

## Requirements
Software and tools used in this workflow:
- R
- MUSCLE (sequence alignment)
- Barrnap (rRNA prediction)
- Phylogenetic analysis packages in R

## Procedure
1. Modification of the intial names, by putting together accessionnumber_organismname (useful for later visualization purposes)
2. Creation of a file with the accession numbers to download the gff3 files.
3. Usage of the tool barrnap that is able to extract for each genome the 16s rRNA sequences present, in particular as output of barrnap we have a fasta file for each genome containing the different copies of 16s rRNA for that genome
4. Creation of a table containing for each accession number the correspondent fasta headers
5. Merge of this table with the one containing accesionnumbers_organismsnames
6. Concatenate all the 16s rRNA sequences into a unique file, and rename the headers using the previously created table, so that the header of the sequence is changed from sequence description to accessionnumber_organismname
7. Creation of the table containing the name of the sequence and the counts of 16s rRNA
8. Building of the phylogenetic tree starting from the 16s rRNA sequences, using MUSCLE as alignment tool, and creation of a tree in which for each genome there is the correspondent number of copies of 16s rRNA (different colors in the legend)
9. Fitting of a model that applies to our phylogenetic tree-traits, choice of the model based on the AIC value
10. Plotting the tree according to the model
11. Prediction of missing traits with phyestimate
-  Phyestimate used in the prediction, using all the available 16s rRNA copies for each organism
- Phyestimate used in the prediction, using only one copy of 16s rRNA for each organism
12. Correlation between predictive and effective trait
