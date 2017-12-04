## Hannah Hatchell
Master's of Bioinformatics, Georgia Institute of Technology  

**Mission Statement:** __Improving early cancer detection using a highly optimized pipeline for the specific detection of low frequency variants.__

## Liquid Biopsy for Early Cancer Detection  
#### Theory

Cancer therapeutics are most effective when the disease is treated during is early stages. Therefore, innovations in early detection techniques hold the key to successful diagnostic of cancer before extensive tumor development occurs. We are seeking to contribute to the computational repertoire of early cancer detection methodologies via detection of low frequency somatic mutations present in circulating tumor DNA present in the blood beginning from the disease's nascent stages. Here, we present the development of a pipeline for whole genome analysis of low frequency variants that can be utilized for cancer detection. 

#### Liquid Biopsy Companies
> [Grail](https://grail.com/)  
> [Guardant Health](http://www.guardanthealth.com/)  
> [Myriad Genetics](https://myriad.com/)  

#### References
1. [Next-Generation Sequencing of Circulating Tumor DNA for Early Cancer Detection](http://www.sciencedirect.com/science/article/pii/S0092867417301150)  

2. [Circulating Tumor DNA Mutation Profiling by Targeted Next Generation Sequencing Provides Guidance for Personalized Treatments in Multiple Cancer Types](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5428730/)

## ahcg_pipeline  
Variant calling pipeline for genomic data analysis  

#### **Test Run**  
[Development and validation of a clinical cancer genomic profiling test based on massively parallel DNA sequencing](https://www.nature.com/nbt/journal/v31/n11/full/nbt.2696.html#methods)
Testing standard variant calling pipeline to accomodate for liquid biopsy-like data processing.  

For data accession click [here](https://www.ncbi.nlm.nih.gov/sra/?term=SRP028580)

#### Requirements

1. [Python3 - version 3.4.1](https://www.python.org/download/releases/3.4.1/)
2. [Trimmomatic - version 0.36](http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.36.zip)
3. [Bowtie2 - version 2.2.9](https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.9/)
4. [Picard tools - version 2.6.0](https://github.com/broadinstitute/picard/releases/download/2.6.0/picard.jar)
5. [GATK - version 3.4](https://software.broadinstitute.org/gatk/download/)
6. [SamTools - version 1.6](https://downloads.sourceforge.net/project/samtools/samtools/1.6/samtools-1.6.tar.bz2?r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fsamtools%2F&ts=1510018121&use_mirror=phoenixnap)
7. [Control-FREEC - version 11.0](https://github.com/BoevaLab/FREEC/archive)
8. [R - version 3.3.2](https://cran.cnr.berkeley.edu/)

#### Reference genome

Reference genomes can be downloaded from [Illumina iGenomes](http://support.illumina.com/sequencing/sequencing_software/igenome.html)
```{sh}
wget ftp://igenome:G3nom3s4u@ussd-ftp.illumina.com/Homo_sapiens/NCBI/GRCh38/Homo_sapiens_NCBI_GRCh38.tar.gz
```

#### Test data

Use the following protocol to download and prepare test dataset from NIST sample NA12878

```{sh}
wget ftp://ftp-trace.ncbi.nih.gov/giab/ftp/data/NA12878/Garvan_NA12878_HG001_HiSeq_Exome/NIST7035_TAAGGCGA_L001_R1_001.fastq.gz
wget ftp://ftp-trace.ncbi.nih.gov/giab/ftp/data/NA12878/Garvan_NA12878_HG001_HiSeq_Exome/NIST7035_TAAGGCGA_L001_R2_001.fastq.gz
gunzip NIST7035_TAAGGCGA_L001_R1_001.fastq.gz
gunzip NIST7035_TAAGGCGA_L001_R2_001.fastq.gz
head -100000 NIST7035_TAAGGCGA_L001_R1_001.fastq > test_r1.fastq
head -100000 NIST7035_TAAGGCGA_L001_R2_001.fastq > test_r2.fastq
```

#### Help

To access help use the following command:

```{sh}
python3 ahcg_pipeline.py -h
```
## Virtual Box Commands

#### Virtual Box Implementation

Verify the name of the virtual box after downloading

```{sh}
VBoxManage list vms
```

Launch the virtual box on the Vannberg server

```{sh}
VBoxManage startvm "Ubuntu-64-DR-AHCG2017" --type headless
```

Power off the virtual box when finished

```{sh}
VBoxManage controlvm "Ubuntu-64-DR-AHCG2017" poweroff soft
```

#### Copying Files to Virtual Box
Files can be transferred from the server to the virtual box using the scp command

```{sh}
scp -r -P 10023 bin/pipeline/ vannberglab@localhost:~/
```
Once transferred, files on the virtual box can be accessed using ssh

```{sh}
ssh vannberglab@localhost -p 10023
```

#### Adjusting Virtual Box Settings 

Cloning the disk

```{sh}
$ vboxmanage clonehd Ubuntu-64-DR-AHCG2017-p10025-disk001.vmdk Ubuntu-64-DR-AHCG2017.vdi --format vdi
```

Increasing disk space

```{sh}
$  vboxmanage modifyhd Ubuntu-64-DR-AHCG2017.vdi --resize 120000
```
