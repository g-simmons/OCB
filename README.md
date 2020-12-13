# AutoCPD: An automated omics compendium preparation pipeline
This toolkit can prepare the transcriptomic compendium, a normalized, format-consistent data matrix across samples from different studies, by collecting the samples in <a href="https://www.ncbi.nlm.nih.gov/sra">Sequencing Read Archive (SRA)</a> database given the topic you are interested in and your target species.
![Figure 1. The entire transcriptomic compendium pipeline](https://github.com/bigghost2054/AutomatedOmicsCompendiumPreparationPipeline/blob/Pipeline_20200307/images/Figure1.png)
Figure 1. The entire transcriptomic compendium pipeline

## Table of Contents
TODO

# Installation (TODO: Rename repo?)
Download the entire repository by:
```
git clone https://github.com/bigghost2054/AutomatedOmicsCompendiumPreparationPipeline
```

## Dependencies

### Software
Make sure the following softwares are installed. We recommend to use Anaconda to ensure that they are installed correctly on $PATH.
```
python==3.6
sra-tools==2.10.8
bowtie==2.3.4
```
### Packages
Make sure to install the following Python packages.
```
biopython==1.74
pandas==0.25
RSeQC==3.0.0
HTSeq==0.11.2
missingpy==0.2.0
scikit-learn==0.20.1
matplotlib==3.0.2
```

# How to Use
This section includes the basic usage of the pipeline. For more detailed tutorial, please refer to ...

## Building Compendium

### Input
In order to build a compendium, the script needs three input arguments
- The path to a sample list file (<a href="https://github.com/bigghost2054/AutomatedOmicsCompendiumPreparationPipeline/blob/Pipeline_20200307/TestFiles/SalmonellaExampleSampleList.csv">Example</a>)
- The path to a gene annotation file (Example, TODO)
- An output compendium name.

### Output
This script will generate a directory with specified compendium name and many files in the directory. There are two outputs that are the most important:
- Normalized data matrix (Filename: '($compendium_name)_NormalizedDataMatrix.csv'): A table in csv format contains normalized gene expression profiles of all samples. Each row represent different genes and each column represent different samples
- Compendium saved in binary format (Filename: '($compendium_name)_projectfile.bin'): A python object contains the normalized gene expression table and recorded parameters. It can be used for optional validation.

### Example
```
cd TranscriptomicPipelines
python build_compendium.py
    ../TestFiles/SalmonellaExampleSampleList.csv
    ../TestFiles/GCF_000006945.2_ASM694v2
    CompendiumExample
```

## Validating Compendium
The pipeline provides several approaches to ensure the quality of the generated compendiums:
- Unsupervised validation
- Unsupervised validation with data matrix
- Supervised validation with correlation
- Supervised validation with knowledge capture
- Supervised validation with published data

# Future Work
In the future, this toolkit will also be capable to process microarray dataset from GEO and ArrayExpress database.

# Citation

# Authors

# License

# Acknowledgements