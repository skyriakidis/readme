# A snakemake pipeline for high-throughput amplicon sequencing

## Tasks

- [ ] Remove hard-coded parameters (add to config build script)
- [ ] Add support for single-end reads
- [ ] Prepare a tutorial for running the pipeline
- [ ] Optimize threads for each rule
- [ ] Add script(s) for reporting summary statistics




## Description

This repository contains scripts that are part of a complete workflow for DNA-seq analysis and mapping reads to a reference genome for the identification of SNPs and designing of haplotypes. 


## Getting started

If you are new to [Snakemake], you might want to start by working the available [tutorial for beginners] with instructions for how to install Snakemake, as well as Miniconda Python 3 and setting an environment with all required software.


## Quick Start:




```bash
#Download files
git clone https://github.com/chollenbeck/snakemake_haps.git

#Change directory to snakemake_haps
cd snakemake_haps

#Installing available environment
conda env create --name [environment_name] --file [/bin/install/environment.yml]

#Activate environment
source activate [environment_name] 

#Start workflow by running snakemake
snakemake
```
 
 

## Data

This repository includes 4 fastq files in [data/fastq_raw/] for use with the workflow as well as a sample fasta file in [data/genome/] which will be used as a reference file for the mapping of the raw reads.  

- Sample 1
	- `test_1.F.fastq.gz` contains the forward mates of the sequenced reads of the first sample
	- `test_1.R.fastq.gz` contains the reverse mates of the sequenced reads of the first sample
	
- Sample 2
	- `test_2.F.faastq.gz` contains the forward mates of the sequenced reads of the second sample
	- `test_2.R.faastq.gz` contains the reverse mates of the sequenced reads of the second sample


## Scripts

[config.yaml] contains links with configuration files and prameters that are used in the workflow
[Snakefile]	contains the 




[Snakefile]: https://github.com/chollenbeck/snakemake_haps/blob/master/Snakefile
[config.yaml]: https://github.com/chollenbeck/snakemake_haps/blob/master/config.yaml
[Snakemake]: https://bitbucket.org/snakemake/snakemake/wiki/Home
[tutorial for beginners]: http://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html