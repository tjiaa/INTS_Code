# INTS_Code
Resistance Gene Location Analysis

This repository provides a three-step pipeline to identify resistance genes located on integrons and transposons within bacterial genomes using the tools abricate and BACANT, followed by a custom integration step. The overall workflow consists of running abricate for resistance gene detection, BACANT for locating integrons and transposons, and a custom integration script to pinpoint the location of resistance genes on mobile genetic elements.

Overview of Analysis Workflow
Step 1: Running Abricate to Locate Resistance Genes
Install abricate following the official documentation.
Use the following command to run abricate on the bacterial genome .fasta file:
Bash abricate --db resfinder --minid=90.0 --mincov=90.0 

The key parameters are:
--db resfinder: Specify the database to use (resfinder).
--minid=90.0: Set the minimum percent identity threshold (90%).
--mincov=90.0: Set the minimum percent coverage threshold (90%).
Record the path of the abricate_output.txt file for subsequent steps.

Step 2: Running BACANT to Locate Integrons and Transposons
Install BACANT following the official documentation.
Run the following command on the same bacterial genome .fasta file:
Bash BACANT -i input_genome.fasta -o BACANT_output/
The results will be stored in the BACANT_output/ directory. Make a note of the path to this output directory for the next step.

Step 3: Integrating Results to Locate Resistance Genes on Integrons and Transposons
Open the Jupyter Notebook file locate_resistance_genes_on_integrons_and_transposons.ipynb to integrate and analyze the results.
Ensure that the paths to abricate_output.txt and the BACANT_output/ directory are correctly specified in the notebook.
Run each cell sequentially to process the data and identify resistance genes located on integrons and transposons.
The final output will be a summary file (resistance_genes_on_integrons_and_transposons.csv) indicating which resistance genes are located on integrons and transposons.

Requirements
Python 3.8+
abricate (for resistance gene detection)
BACANT (for locating integrons and transposons)
