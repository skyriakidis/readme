# A tutorial for a complete variant calling and haplotype designing workflow


# 1) Description

This is a tutorial to learn how to use the Snakemake workflow for mapping reads, call high quality variants and design haplotypes accurately. 

This tutorial is using two samples and one fasta file as a reference.

# 2) First steps

1. Downloading and Installing (Ana|mini)conda:
- [Anaconda]
- [Miniconda]

### For installing Anaconda:

- [Curl] is needed so if not installed you can install it by typing:
```sh
sudo apt install curl	
```
	
- Installing Anaconda:
```sh
curl -o /tmp/Anaconda.sh https://repo.continuum.io/archive/Anaconda3-5.1.0-Linux-x86_64.sh && bash /tmp/Anaconda.sh
```

or

- Download the available version of Anaconda from https://www.continuum.io/downloads
and
- Run the installer by typing:
```sh
bash Anaconda.sh
```

### For installing Miniconda3:

- Installing Miniconda3:
```sh
curl -o /tmp/miniconda.sh https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh && bash /tmp/miniconda.sh
```
or

- Download the available version of Miniconda3 from https://conda.io/miniconda.html
and
- Run the installer by typing:
```sh
bash Miniconda3-latest-Linux-x86_64.sh
```

2. Installing Snakemake using [Bioconda] channel:
```sh
conda install -c bioconda snakemake
```
	
 
	

	
	


#Installation of conda
conda install -c bioconda snakemake




[Anaconda]: https://www.continuum.io/downloads
[Miniconda]: https://conda.io/miniconda.html
[Curl]: https://www.tutorialspoint.com/unix_commands/curl.htm 
[Bioconda]: https://bioconda.github.io/
