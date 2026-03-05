# 16S-rRNA-copy-number-prediction
The aim is the prediction of the number of 16S rRNA gene copies in bacterial genomes, using comparative phylogenetics methods.
The analysis focuses on bacteria belonging to the class Alphaproteobacteria and uses available genomes to infer the number of 16S rRNA copies in new genomes.

## :twisted_rightwards_arrows: Workflow overview
<img width="453" height="665" alt="workflow_prediction_16srRNA drawio" src="https://github.com/user-attachments/assets/3c48e610-0ea9-4163-93c5-21251aeaf18d" />

## How to use 🔧

**Input required**: 
a table containing two columns:
- accession numbers
- organism names

**Output**:
Prediction of the number of 16S rRNA copies for new genomes

## Requirements
Software and tools used in this workflow:
- R
- MUSCLE (sequence alignment)
- Barrnap (rRNA prediction)
- Phylogenetic analysis packages in R

## Procedure
1. Modification of the initial names, by putting together accessionnumber_organismname (useful for later visualization purposes)
2. Creation of a file with the accession numbers to download the gff3 files.
3. Usage of the tool barrnap that is able to extract for each genome the 16S rRNA sequences present, in particular as output of barrnap we have a fasta file for each genome containing the different copies of 16S rRNA for that genome
4. Creation of a table containing for each accession number the correspondent fasta headers
5. Merge of this table with the one containing accesionnumbers_organismsnames
6. Concatenate all the 16S rRNA sequences into a unique file, and rename the headers using the previously created table, so that the header of the sequence is changed from sequence description to accessionnumber_organismname
7. Creation of the table containing the name of the sequence and the counts of 16S rRNA
8. Building of the phylogenetic tree starting from the 16S rRNA sequences, using MUSCLE as alignment tool, and creation of a tree in which for each genome there is the correspondent number of copies of 16S rRNA (different colors in the legend)
9. Fitting of a model that applies to our phylogenetic tree-traits, choice of the model based on the AIC value
10. Plotting the tree according to the model
11. Prediction of missing traits with phyestimate
-  Phyestimate used in the prediction, using all the available 16S rRNA copies for each organism
- Phyestimate used in the prediction, using only one copy of 16S rRNA for each organism
12. Correlation between predictive and effective trait
