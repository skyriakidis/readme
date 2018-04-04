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
conda env create --name *environment_name* --file /bin/install/environment.yml

#Activate environment
source activate *environment_name* 

#Start workflow by running snakemake
snakemake
```
 
 

## Data

This repository includes 4 fastq files in [data/fastq_raw] folder for use with the workflow as well as a sample fasta file in [data/genome] which will be used as a reference file for the mapping of the raw reads.

- Sample 1
	- `test_1.F.fastq.gz` contains the forward mates of the sequenced reads of the first sample
	- `test_1.R.fastq.gz` contains the reverse mates of the sequenced reads of the first sample
	
- Sample 2
	- `test_2.F.fastq.gz` contains the forward mates of the sequenced reads of the second sample
	- `test_2.R.fastq.gz` contains the reverse mates of the sequenced reads of the second sample


## Scripts

-[config.yaml] contains links with configuration files and parameters that are used in the workflow.

-[Snakefile] contains the rules that are used in the workflow, written as python scripts and stored in [bin/snakefiles].

## Snakefiles

-[raw.py] creates links with the reference genome and the fastq files for downstream analysis by the workflow.

-[folders.py] creates folders for all output files produced by each step of the workflow.

-[qc.py] QC.py by using Trimmomatic removes Illumina adapters that can cause a problem downstream analysis and the identification of high quality SNPs. Additionally, Trimmomatic trims low quality regions of reads. Apart from Trimmomatic, qc.py contains a quality control step using FastQC tool to confirm the high quality of trimmed reads.

-[map.py] 
 
 






[Snakefile]: https://github.com/chollenbeck/snakemake_haps/blob/master/Snakefile
[config.yaml]: https://github.com/chollenbeck/snakemake_haps/blob/master/config.yaml
[data/fastq_raw]: https://github.com/chollenbeck/snakemake_haps/tree/master/data/fastq_raw
[data/genome]: https://github.com/chollenbeck/snakemake_haps/tree/master/data/genome
[raw.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/raw.py
[folder.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/folders.py
[map.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/map.py
[qc.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/qc.py
[bin/snakefiles]: https://github.com/chollenbeck/snakemake_haps/tree/master/bin/snakefiles 
[Snakemake]: https://bitbucket.org/snakemake/snakemake/wiki/Home
[tutorial for beginners]: http://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html
