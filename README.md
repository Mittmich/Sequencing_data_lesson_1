# Python Journal Club 20.11.19 - Sequencing Data Analysis

The goal of this journal club is to introduce basic sequencing data formats as well as formats of genomic features and learn how to work with them in python.

## Datafiles

File | Format |Explanations
------------ | ------------- |-------------
SMC3_chip_seq.bed | BED | Chip-seq data of SMC3 in HeLa cells synchronized to G2
CTCF_chip_seq.bed | BED | Chip-seq data of CTCF in HeLa cells synchronized to G2
RAD51_chip-seq.bw | bigWig | Chip-seq data of RAD51 in U2OS cells expressing a restriction enzyme
XRCC4_chip-seq.bw | bigWig | Chip-seq data of XRCC4 in U2OS cells expressing a restriction enzyme
Restriction_cut_sites.bed | BED | Locations where the restriction enzyme in U2OS cells is introducing cuts
SMC3_chip_seq.bw | bigWig | BigWig file of the SMC3 chip-seq data in HeLa cells synchronized to G2

## Notebooks

Both the notebook for Example 1 and the notebook for Example 2 can be run in the singularity [container](https://hub.docker.com/repository/docker/gerlichlab/mmhic) with tag "release-0.8". Also you should have everything you need for the homework examples.

## Resources

The APIs that we will use are the following

### [Pybedtools](https://daler.github.io/pybedtools/)
### [Pybigwig](https://github.com/deeptools/pyBigWig)

## Homework