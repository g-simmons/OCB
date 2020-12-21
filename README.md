# AutoCPD: An automated omics compendium preparation pipeline
This toolkit can prepare the transcriptomic compendium, a normalized, format-consistent data matrix across samples from different studies, by collecting the samples in <a href="https://www.ncbi.nlm.nih.gov/sra">Sequencing Read Archive (SRA)</a> database given the topic you are interested in and your target species.
![Figure 1. The entire transcriptomic compendium pipeline](https://github.com/bigghost2054/Omics-Compendium-Builder-OCB/blob/master/images/Figure1.png)
**Figure 1. The entire transcriptomic compendium pipeline.** The process consists of 6 steps: **1**, Metadata preparation by extracting run information from SRA. **2**, Downloading sequencing data in FASTA format. **3**, Aligning sequences with reference genomes. **4**, Generating gene expression profile for each run given the corresponding sequence direction information (BED) and gene annotation. **5**, Normalizing gene expression profile table. **6**, Different approaches for validating the quality of the generated compendium.

# Installation
Download the entire repository:
```
git clone https://github.com/bigghost2054/Omics-Compendium-Builder-OCB
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
The pipeline consists of two components: Compendium construction and validation. The pipeline builds a compendium using the sample lists and gene annotations provided by users. Then it provides different validation approaches to validate the statistical siginificance and usefulness of the generated compendiums. For more detailed usage, see this [step-by-step tutorial](./STEP-BY-STEP.md).

## Constructing Compendium

### Input
In order to build a compendium, the script needs three input arguments:
- The path to a sample list file ([Example](./TestFiles/SalmonellaExampleSampleList.csv))
- The path to a gene annotation file (Example, TODO)
- An output compendium name.

### Output
This script will generate a directory with specified compendium name and many files in the directory. There are two outputs that are the most important:
- Normalized data matrix: A CSV table that contains normalized gene expression profiles of all samples. Each row represents different genes and each column represents different samples. The output is stored in '($compendium_name)_NormalizedDataMatrix.csv'.
- Compendium in binary format: A python object that contains the normalized gene expression table and the recorded parameters. It can be used for optional validation. The output is stored in '($compendium_name)_projectfile.bin'.

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

Please refer to [validation totorial](./VALIDATION.md).

# Future Work
In the future, this toolkit will also be capable to process microarray dataset from GEO and ArrayExpress database.

# Citation

# Authors

# License
This project is licensed under the Apache 2.0 License - see the [LICENSE](./LICENSE) file for details.

# Acknowledgements
