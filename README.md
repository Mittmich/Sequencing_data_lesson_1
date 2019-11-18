# Python Journal Club 20.11.19 - Sequencing Data Analysis

The goal of this journal club is to introduce basic sequencing data formats as well as formats of genomic features and learn how to work with them in python.

## Datafiles

Note: Datafiles are not part of the repository, but reside on our server. See the example ipython notebooks for the paths.


File | Format |Explanations
------------ | ------------- |-------------
SMC3_chip_seq.bed | BED | Chip-seq data of SMC3 in HeLa cells synchronized to G2
CTCF_chip_seq.bed | BED | Chip-seq data of CTCF in HeLa cells synchronized to G2
RAD51_chip-seq.bw | bigWig | Chip-seq data of RAD51 in U2OS cells expressing a restriction enzyme
XRCC4_chip-seq.bw | bigWig | Chip-seq data of XRCC4 in U2OS cells expressing a restriction enzyme
Restriction_cut_sites.bed | BED | Locations where the restriction enzyme in U2OS cells is introducing cuts (only a 2 of the original 40 sites provided)
SMC3_chip_seq.bw | bigWig | BigWig file of the SMC3 chip-seq data in HeLa cells synchronized to G2

## Notebooks


Both the notebook for Example 1 and the notebook for Example 2 can be run in out Hi-C singularity [container](https://hub.docker.com/repository/docker/gerlichlab/mmhic) with tag "release-0.8". To check out how to start the container, check out our wiki.

### Example 1

Example 1 is thought to be a small introduction into the pybedtools API for genomic interval data. Furthermore, it aims to illustrate the general concept of how to work with (possibly) unkown and complex filetypes in python. In short, this is done by using a suitable python API that provides an interface to the filtype and allows conversion into on of the familiar python objects such as pandas dataframes or numpy arrays.

### Example 2

Example 2 extends the principles of example 1 to a further filetype, BigWig. These files are in a [binary format](https://en.wikipedia.org/wiki/Binary_file), so are not immediately accessible for reading. This highlights that we need an interface to make any sense of the data, which in this case is the pybigwig module. This example then combines the interface to bedfiles and pybigwig files to generate pileups of SMC3 Chip-seq data at called chip-seq peaks.


## Resources

The APIs that we will use are the following

### [Pybedtools](https://daler.github.io/pybedtools/)

Is a python wrapper around the command line tool [bedtools](https://bedtools.readthedocs.io/en/latest/), which allows working with genomic interval data.


### [Pybigwig](https://github.com/deeptools/pyBigWig)

Python API for the [BigWig format](https://genome.ucsc.edu/goldenpath/help/bigWig.html).

### [Bioframe](https://github.com/mirnylab/bioframe)

Similar to bedtools, but implements interfaces for downloading data from the [UCSC hg19 genome annotation database](http://hgdownload.cse.ucsc.edu/goldenPath/hg19/database/).


## Homework

### Example 1
**(a)** Count the number of of SMC3 peaks that do not overlap CTCF per chromosome and genome-wide. (For this you will need to look at the pybedtools API documentation)

**(b)** Plot the distribution of peak-sizes of SMC3. (For this it might be usefule to check out the matplotlib chapter in our python data science handbook, especially the part about histograms.)

**(c)** Plot the distribution of distances between peaks. (Take care that you do not calculate distances accross chromosomes!)

### Example 2
This example uses chip-seq data from this [paper](https://www.nature.com/articles/nsmb.2796). In short, they have a cell-line with an inducible restriction enzyme that will cut ~40 times in the human genome. In cells, where this restriction enzyme was induced, they perforemd Chip-seq against XRCC4 (a part of the DNA ligase that repairs NHEJ junctions) and Rad51 (a central part of the homology directed repair machinery to estimate the DNA pathway choice at each location.

**(a)** Plot the distribution of XRCC4 and Rad51 at the two provided restriction cut-sites in a 100bp window around the cut-site (-500bp to +500bp). Can you guess which site is preferrably repaired by HDR and which by NHEJ?

**(b)** Since Rad51 is a protein that binds in a rather broad way to DNA, it might be more useful to zoom out our view-points a little bit. Plot the distribution of XRCC4 and Rad51 at 200kb around each cut-sites (-100kb to +100kb). Why does your plotting function hang? What could be a solution? (Hint: You may want to use either [np.digitize](https://docs.scipy.org/doc/numpy/reference/generated/numpy.digitize.html) or [pandas.cut](https://pandas.pydata.org/pandas-docs/version/0.23.4/generated/pandas.cut.html))