# Filtering annotated exome variants

## Basic information  
When calling variants from aligned exome data, the variants are typically saved in VCF files. These are text based files and so can be read in any text editor like Notepad or preferably Notepad++. Since one line contains data on one variant it is best to use a program that either doesn't wordwrap or allows it to be turned off. An example VCF file is [here](data/VCF_Header.txt). This file contains all the descriptor columns plus a few variant entires. While the file is human readable, its format is not that easy to read especially considering a typical exome data set may have about 35k variants. 

Each variant in an unannotated VCF files always contains data on it's position, RS ID, reference and alternative alleles. It may also contain a quality score and whether it passed filtering. This data is stored 7 columns of data, with the eighth column containing a series of optional data values as key: data pairs separated by a __;__ such as BaseQRankSum=-0.134;ClippingRankSum=-0.325. A description of each key:value pair is given in the head section for example:

##INFO=<ID=BaseQRankSum,Number=1,Type=Float,Description="Z-score from Wilcoxon rank sum test of Alt Vs. Ref base qualities">  
##INFO=<ID=ClippingRankSum,Number=1,Type=Float,Description="Z-score From Wilcoxon rank sum test of Alt vs. Ref number of hard clipped bases">

The ninth column contains a series of option key such as GT:AD:DP with the remaining columns containing the relevant, for instance GT:AD:DP in the ninth column and 0/1:15,13:28 in the tenth column is equivalent to GT = 0/1, AD = 15,13 and DP = 28. The definition of GT, AD and DP is in the header section as: 

##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">   
##FORMAT=<ID=AD,Number=R,Type=Integer,Description="Allelic depths for the ref and alt alleles in the order listed">  
##FORMAT=<ID=DP,Number=1,Type=Integer,Description="Approximate read depth (reads with MQ=255 or with bad mates are filtered)">

The genotypes are typically 1/1 for homozygous alternative allele, 0/1 heterozygous and 0/0 wild type (generally not included)

As can be seen from the description above and from viewing the [eaxmple file](data/VCF_Header.txt), VCF files can be hard to interpret. This can become even worse when viewing annotated VCF, such as this [one](data/VEP_annotated_VCF_header.txt) which was annotated by VEP. Consequently, variant data sets are generally filtered using a program or by arranging the data as tab-delimited text files which can be viewed as a spreadsheet. The chrng-*.txt files are examples of variant data from chromosome 2, 233 MB to 234 MB  annotated by Annovar.

## Screening variants by eye

### Getting the data 

The chrng-*.txt files in the data folder contain data two affected siblings chrng-9 and chrng-10 and their parents and unaffected sibling. Download each file by going to the [data folder](data/) and then selecting each file in turn and pressing the download icon in the top right of the webpage 