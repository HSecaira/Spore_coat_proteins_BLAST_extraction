# Spore_coat_proteins_BLAST_extraction

This repository contains Biopython scripts to extract significant pBLAST hits (i.e. proteins) using the protein id. These scripts were used as part of the project Diversity and Evolutionary Dynamics of Spore Coat Proteins on Bacillales and Bacillus. 

The scripts require Jupyter Notebook, Python and Biopython. Aditionally, you need a .xml file containing the local BLAST results and a genbank file containing the genome of the species from which you want to extract the genes. 

Files provided:
  - Bacillus_extract_genes_scripts.ipynb
  - result_Bacillus_xiamenensis_VV3.xml (BLAST results)
  - cotE_aligned.fas
  - Genbank file of species used: https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP017786.1 
  
  
## Steps to extract genes from pBLAST results for each genome/species

1. Check and save significant pBLAST results
    - In this step, we will create a new file to save only the significant BLAST results (protein accesion id, sequence, accession title).
      - (Extra) In local BLAST you can use the following lines to obtain a similar BLAST file containing results:
        - Create a database: makeblastdb -in genome.fasta -parse_seqids -dbtype prot
        - Query: blastp -query proteins.fas -db genome.fasta -out result_BLAST.xml -outfmt "5"      
2. Extract genes from genbank files (genomes) using Protein Accesion from significant BLAST results
    - In this step, we will extract all the genes using protein acession id (step 1) from a genbank file and save them in a new file.
3. Change headers id from extracted genes (optional but helpful in future steps)
    - In this step, we can change each sequence id, from protein acession id to gene name. 
    
## Steps to create a database of the same gene from multiple genomes/species (used for "Selection methods")

1. Extract the same gene from multiple files (i.e. species)
    - Let suppose we extracted all the coat proteins for each member of the Pumilus group. Now, in this step, we will create a single file that contain only one gene from all the members of the group.
2. Delete stop codons of a gene database
    - In this step, we will create a new file gene database with its sequences without stop codons, since it is required by some methods (MEME, BUSTED, CodeML).
    
### **All files must be in the same location, unless you specify the location!**
