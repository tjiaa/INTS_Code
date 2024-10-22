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
Python package numpy, pandas are needed
abricate (for resistance gene detection)
BACANT (for locating integrons and transposons)



TEST DATA SET
This repository provides a test dataset consisting of 10 publicly available bacterial genomes. These genomes have been prepared to serve as a test set for validating the co-localization of antimicrobial resistance genes (ARGs) and integrons/transposons .

Data Preparation
1、Antimicrobial Resistance Genes Data: We used Abricate to identify the antimicrobial resistance genes across all 10 bacterial genomes.
2、Mobile Genetic Elements Data: We used Bacant to identify mobile genetic elements (MGEs) for these same 10 bacterial genomes.

Once you have all the required data files, you can proceed to run our co-localization code. Please make sure to update the file paths in the script to match your local environment before executing the code.
This test dataset ensures you have all the necessary inputs to validate the functionality of our resistance gene-mobile element co-localization method.
For any questions or issues, feel free to open an issue in the GitHub repository.
