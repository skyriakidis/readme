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

#Create config.yaml consisting a list of the samples and their paths in /data/fastq_raw/, as well as mapping and variant filtering parameters
python /bin/scripts/build_hap_config.py

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

-[qc.py] qc.py by using Trimmomatic removes Illumina adapters that can cause a problem downstream analysis and the identification of high quality SNPs. Additionally, Trimmomatic trims low quality regions of reads. Apart from Trimmomatic, qc.py contains a quality control step using fastQC tool to confirm the high quality of trimmed reads producing figures and tables with statistics which are explained in [fastQC] help page.

-[map.py] This script contains the full workflow for mapping the reads to a reference genome by using [BWA-MEM] mapper (Li, 2009) and [FreeBayes] (Garrison et al., 2012) variant caller. 
- Steps
	1) Indexing of the reference genome.
	2) Mapping the trimmed reads against the reference genome and sorting the output [BAM] file.
	3) Apply [SAMtools] -fixmate and -markdup utilities to sorted BAM files for the removal of potential PCR duplicates. The output file of this step must be indexed.
	4) For variant calling, the output BAM files from mapping each sample to the reference genome must be merged and indexed.

-[variant_calling.py] contains the workflow for the identification of variants from the produced BAM files. Initially this script splits the reference sequence into  multiple components for faster variant analysis. FreeBayes is the variant caller which requires as input files the indexed merged BAM file and produes a VCF file with raw variants. A filtering procedure is included in this script to remove low quality variants from the final variant set.

-[haplotype.py] 

-[clean.py] removes all uneccessary files and folders created thoughout the analysis




## References

Garrison E, Marth G. Haplotype-based variant detection from short-read sequencing. arXiv preprint arXiv:1207.3907 [q-bio.GN] 2012

Li H. and Durbin R. (2009). Fast and accurate short read alignment with Burrows-Wheeler Transform. Bioinformatics, 25(14), 1754-1760.




[Snakefile]: https://github.com/chollenbeck/snakemake_haps/blob/master/Snakefile
[config.yaml]: https://github.com/chollenbeck/snakemake_haps/blob/master/config.yaml
[data/fastq_raw]: https://github.com/chollenbeck/snakemake_haps/tree/master/data/fastq_raw
[data/genome]: https://github.com/chollenbeck/snakemake_haps/tree/master/data/genome
[raw.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/raw.py
[folders.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/folders.py
[map.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/map.py
[qc.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/qc.py
[variant_calling.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/variant_calling.py
[haplotype.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/haplotype.py
[clean.py]: https://github.com/chollenbeck/snakemake_haps/blob/master/bin/snakefiles/clean.py
[bin/snakefiles]: https://github.com/chollenbeck/snakemake_haps/tree/master/bin/snakefiles 
[Snakemake]: https://bitbucket.org/snakemake/snakemake/wiki/Home
[tutorial for beginners]: http://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html
[fastqc]: https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/
[BAM]: http://samtools.github.io/hts-specs/SAMv1.pdf
[SAMtools]: http://samtools.sourceforge.net/
[BWA-MEM]: http://bio-bwa.sourceforge.net/bwa.shtml
[FreeBayes]: https://github.com/ekg/freebayes









