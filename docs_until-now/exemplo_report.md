---
title: "Study Report - Overview of 16S rRNA (Qiime2-2018.2)"
author: "Almeida, R.V.M."
date: "`r Sys.Date()`"
---

# Introduction

## Primary analysis

The V3 region is the most informative of the 16S and the V3-V4 amplicons usually present good resolution results to determine the microbial communities that inhabit the samples of interest. The data used in this analysis were sequenced on an *Illumina MiSeq* using the *Faecal Microbiome Indian* Samples hypervariable region 3-4 (V3-V4) 16S rRNA sequencing protocol. 

Image analysis was performed in real time by the MiSeq Control Software (MCS) v2.6.2.1 and Real Time Analysis (RTA) v1.18.54, running on the instrument computer. RTA performs real-time base calling on the MiSeq instrument computer. Then the Illumina bcl2fastq 2.20.0.422 pipeline was used to generate the sequence data. The data generated here meet the AGRF quality standards.


## Experimental Design:

+ **46 patient samples:**
    + 23 disease samples (VL) - gDNA from stool
    + 23 healthy control samples (EC) - gDNA from stool


+ **14 sequencing control samples:**
    + 8 negative extraction control samples (CONT) - four in duplicate
    + 5 mock community samples (MOCK) - containing increasing amounts of spiked human DNA
    + 1 human DNA sample (HCONT) - containing the human DNA used to spike the mock community


The data yield is as follows:

> **300bp Paired End - Flowcell ID: 000000000-BPDNR**

Lane	  | Sample Name	 | Paired Reads	 | Data Yield (bp)
:------: | ----------- | ------------ | :---------------:
1       | EC1 | 332,448 | 0.20 Gb
1       | EC2 | 395,078 | 0.24 Gb
1       | EC3 | 276,057 | 0.17 Gb
1       | EC4 | 97,194 | 0.06 Gb
1       | EC5 | 257,365 | 0.15 Gb
1       | EC6 | 136,796 | 0.08 Gb
1       | EC7 | 67,196 | 0.04 Gb
1       | EC8 | 154,800 | 0.09 Gb
1       | EC9 | 215,810 | 0.13 Gb
1       | EC10 | 212,690 | 0.13 Gb
1       | EC11 | 393,147 | 0.24 Gb
1       | EC12 | 362,892 | 0.22 Gb
1       | EC13 | 388,141 | 0.23 Gb
1       | EC14 | 434,361 | 0.26 Gb
1       | EC15 | 116,133 | 0.07 Gb
1       | EC16 | 104,769 | 0.06 Gb
1       | EC17 | 118,000 | 0.07 Gb
1       | EC18 | 146,746 | 0.09 Gb
1       | EC19 | 137,747 | 0.08 Gb
1       | EC20 | 179,706 | 0.11 Gb
1       | EC21 | 198,200 | 0.12 Gb
1       | EC22 | 812,329 | 0.49 Gb
1       | EC23 | 228,203 | 0.14 Gb
1       | VL1 | 249,058 | 0.15 Gb
1       | VL2 | 244,395 | 0.15 Gb
1       | VL3 | 214,364 | 0.13 Gb
1       | VL4 | 212,774 | 0.13 Gb
1       | VL5 | 243,170 | 0.15 Gb
1       | VL6 | 168,894 | 0.10 Gb
1       | VL7 | 713,489 | 0.43 Gb
1       | VL8 | 525,995 | 0.32 Gb
1       | VL9 | 512,278 | 0.31 Gb
1       | VL10 | 561,668 | 0.34 Gb
1       | VL11 | 235,037 | 0.14 Gb
1       | VL12 | 101,174 | 0.06 Gb
1       | VL13 | 187,606 | 0.11 Gb
1       | VL14 | 123,470 | 0.07 Gb
1       | VL15 | 152,389 | 0.09 Gb
1       | VL16 | 171,153 | 0.10 Gb
1       | VL17 | 116,218 | 0.07 Gb
1       | VL18 | 167,670 | 0.10 Gb
1       | VL19 | 238,867 | 0.14 Gb
1       | VL20 | 336,417 | 0.20 Gb
1       | VL21 | 430,654 | 0.26 Gb
1       | VL22 | 299,134 | 0.18 Gb
1       | VL23 | 517,757 | 0.31 Gb
1       | CONT1 | 55,451 | 0.03 Gb
1       | CONT1rep | 12,307 | 0.01 Gb
1       | CONT2 | 8,726 | 0.01 Gb
1       | CONT2rep |	166 | 0.00 Gb
1       | CONT3 | 693 | 0.00 Gb
1       | CONT3rep | 30,176 | 0.02 Gb
1       | CONT4 | 23,831 | 0.01 Gb
1       | CONT4rep | 17,911 | 0.01 Gb
1       | HCONT | 7,007 | 0.00 Gb
1       | MOCKA | 192,487 | 0.12 Gb
1       | MOCKB | 224,945 | 0.14 Gb
1       | MOCKC | 242,588 | 0.15 Gb
1       | MOCKD | 382,072 | 0.23 Gb
1       | MOCKE | 193,326 | 0.12 Gb
|       | **Total** | 13,881,125 | 8.36 Gb


### Obtaining and importing data from AGRF NextGen-Seq (*Illumina*)  

Download the sequence reads that we’ll use in this analysis. The data used in this analysis is derived from a **Fecal Microbiome Study** with 50 samples from Indian VL patients and endemic healthy controls . 

Below is a brief description of the files format.

`<sample_name>_<flowcell_ID>_<index>_<lane>_<readNum>_fastq.gz` - compressed FastQ formatted sequence file containing untrimmed 300 bp reads, where `<readNum>` specifies the first or second read of the pair.

These files contain the read sequence output with the corresponding *Illumina quality scores*. The quality is encoded in *symbolic* ASCII format in the following way: char (phred-like quality score + 33).    

>Obs.: For some reason, AGRF has added a '0' to the end of every sample ID, but subsequently during preprocessing that '0' is removed.

### AGRF Data Verification

The *checksum* information of the files included has been generated using the md5sum program. The calculated checksums of your data files are included in the `checksums.md5` file.

To test the integrity of your files, type the following command while in the directory containing `checksums.md5`:

```bash 
md5sum -c checksums.md5
```

___

# Pre-Processing 


All *commands* were based on the use of QIIME™ 2 software to perform an analysis of human microbiome samples. This documentation assumes have installed QIIME™ 2 using the procedures in [documentation of software](http://qiime2.org/).

Before beginning this analysis, create a new directory and change to that directory.  

```bash
mkdir VL-analysis
cd VL-analysis
```

Then create a subdirectory and copy the files with the reads obtained from the sequencing to it.

```bash
mkdir VL-data
cp -v ~/ref_code_seq/*.fastq.gz /VL-data/
```

After copying the fastaq files to the new directory, in this case, it was necessary to rename the samples to the correct name format associated analysis (*Casava 1.8 paired-end*). As mentioned earlier, by default the file names of this format needed to display `001.fastq.gz` as the final part of its extension, after the `<readNum>`.

For this was used the command called `rename`.

```bash
rename 's/.fastq.gz/._001.fastq.gz/' \*.gz
```

Finally, the '0' previously added by the AGRF to the end of each sample ID was also removed.


## Sample metadata

Define which information should be part of the *sample-metadata* file. Save the `sample-metadata.tsv` file in the *analysis folder*.

<!-- descrever em uma tabela ou de outra forma -->


### Importing data | sequence with quality information

Import the sequence reads that we’ll use in this analysis.


```bash
qiime tools import \
  --type 'SampleData[PairedEndSequencesWithQuality]' \
  --source-format CasavaOneEightSingleLanePerSampleDirFmt \
  --input-path VL-data \
  --output-path VL_faecal_v1.qza
```  
___

## Amplicon Primers

As said before the gene specific sequences used in this protocol target the 16S v3 and v4 region. Furthermore, *Illumina* adapter overghang nucleotide sequences are added to the gene specific sequences. the full length primer sequence, using standard IUPAC nucleotide nomenclature, to follow the protocol targetting the region:

`16S Amplicon PCR Forward Primer = 5' TCGTCGG........CAG`(Info. of Prime Restrict!)

`16S Amplicon PCR Reverse Primer = 5' GTCTCGT........TCC`(Info. of Prime Restrict!)


The method consists of the overhang adapter sequence to be added to the locus-specific primer for the region to be targeted. The Illumina overhang adapter sequences to be added to locu-specific sequences are (reference):

`Forward overhang: 5’ TCGTCG...AGAGACAG   [locus specific sequence]` (Info. of locus Restrict!)

`Reverse overhang: 5’ GTCTCG...GAGACAG  [locus specific sequence]` (Info. oflocus Restrict!)

As an essential step for continuing the process it is necessary that such sequences be removed from the final dataset for analysis.

___

### Remove adapter and primers sequences from high-throughput sequencing reads | 2-steps

Find and remove fist the adapters in demultiplexed paired-end sequences, then repeat the same command with the output to remove the primers. The QIIME™ 2 features a plugin that uses cutadapt to work with adapters (e.g. barcodes, primers) in sequence data.


#### 1st Step - Find and remove adapters

```bash
qiime cutadapt trim-paired \
  --i-demultiplexed-sequences VL_faecal_v1.qza \
  --p-cores 16 \
  --p-front-f TCGT.....ACAG \
  --p-front-r GTCT.....ACAG \
  --p-error-rate 0.1 \
  --o-trimmed-sequences adapter-trimmed-VL_faecal \
  --verbose
```  
##### 2nd Step - Repeat Step 1 for primers

```bash
qiime cutadapt trim-paired \
--i-demultiplexed-sequences adapter-trimmed-VL_faecal.qza \
--p-cores 16 \
--p-front-f CC.......CAG \
--p-front-r GA.......TCC \
--p-error-rate 0.1 \
--o-trimmed-sequences primer-trimmed-VL_faecal \
--verbose
```

After this two-step process was obtained the file `primer-trimmed-VL_faecal.qza` with trimmed demultiplexed paired-end sequences. During the triming process all searches for adapter sequences are error tolerant. Allowed errors are mismatches, insertions, and deletions. The level of error tolerance is adjusted by specifying the *maximum error rate*, for this analysis the default value of 0.1 (= 10%) was used.

___

## Summary of the demultiplexing sequence data


After demultiplexing, it’s useful to generate a summary of the demultiplexing results. Create a *visualization* file with a sequence *demultiplexed* counts summary. The plugin of QIIME™ 2 (`qiime demux summarize`) will generate a `.qzv` file. 

```bash
qiime demux summarize \
  --verbose \
  --i-data primer-trimmed-VL_faecal.qza \
  --o-visualization demux-summary-VL_faecal.qzv
```

With this result it is possible to determine the number of sequences that were obtained per sample, as well as to show a summary of the distribution of sequence qualities in each position. Can be view these files with command: 

```bash
qiime tools view demux-summary-VL_faecal.qzv
```

![Quality of the Forward Reads](https://github.com/RicardoVictorm/Microbiome_analysis/blob/master/fig_report/version2_figs/demux%20summary%20VL_faecal_v2_f.png)

![Quality of the Reverse Reads](https://github.com/RicardoVictorm/Microbiome_analysis/blob/master/fig_report/version2_figs/demux%20summary%20VL_faecal_v2_r.png){width=85%}

This views (**Fig.01-02**) shows an overview of the range of quality values across all bases at each position. It can be observed that the quality of the readings seems to tend to decrease the larger their size in the distribution, which is evident at the end of both figures.


# Quality Control Methods

QIIME™ 2 *plugins* are available for several quality control methods, including [DADA2](https://www.ncbi.nlm.nih.gov/pubmed/27214047). This is a pipeline for detecting and correcting (where possible) Illumina amplicon sequence data. As implemented in the `q2-dada2 plugin`, this quality control process will additionally filter any phiX reads (commonly present in marker gene Illumina sequence data) that are identified in the sequencing data, and will filter chimeric sequences.

Here the quality seems relatively low in the first few bases, and then seems to stay relatively high through the end of the reads.

## DADA2 for denoise-paired

```bash
qiime dada2 denoise-paired \
  --verbose \
  --p-n-threads 16 \
  --i-demultiplexed-seqs primer-trimmed-VL_faecal.qza \
  --o-table table \
  --o-representative-sequences rep-seqs \
  --p-trim-left-f 0 \
  --p-trim-left-r 7 \
  --p-trunc-len-f 293 \
  --p-trunc-len-r 253
```

Based on the *visualization* seen in `demux-summary-VL_faecal.qzv` the values were chosen for `--p-trunc-len` and `--p-trim-left`. This choice was made setting the threshold above 30 (score phred) quality criterion as the average acceptable on the distribution of sequence qualities. Therefore, it reads with more than 293 bps in forward Sequencing and 253 bps in reverse size in the distribution begin to drop in quality. Although the initial baseline quality score (Median) appears to be high it was decided to remove only the first 7 bp Reverse as a guarantee of not having in the analysis reads from be a poor read.

Next, it was generate a summary of the **FeatureTable[Frequency]** and **FeatureData[Sequence]** artifact. For this it is necessary the filtered/denoised data using the `qiime feature table` function.

#### feature table construction | FeatureTable[Frequency]

```bash
qiime feature-table summarize \
  --verbose \
  --i-table table.qza \
  --o-visualization table.qzv \
  --m-sample-metadata-file sample-metadata.tsv
```
#### feature table construction | FeatureData[Sequence]

```bash
qiime feature-table tabulate-seqs \
  --verbose \
  --i-data rep-seqs.qza \
  --o-visualization rep-seqs.qzv
```

<center>
![](https://github.com/RicardoVictorm/Microbiome_analysis/blob/master/fig_report/version2_figs/table%20qzv_View.png){width=50%}
![Frequency per sample](https://github.com/RicardoVictorm/Microbiome_analysis/blob/master/fig_report/demux%20summary%20VL_Bar_View.png){width=60%}
</center>


![Details of the view.qiime2.org - number of sample per group](~/Desktop/Results_v4/fig_report/table qzv_number of samples.png)

The above code produced two `.qzv` files that can be scanned. Alternatively the plugin `qiime tools view`, we can see the artifacts and views of QIIME™ 2 in [view.qiime2.org](https://view.qiime2.org/) uploading files or providing URLs. The result obtained with the view of QIIME 2 presents an overview of the total samples analyzed and distribution of their frequency, as shown above.

The **“interactive Sample Detail”** tab (**Fig.03**) of the viewer gives you a way to explore how rarefaction depths (subsampling) impact the data (i.e. which samples will be dropped).


___


# Phylogenetic Classification


## Generate a Tree for Phylogenetic diversity analyses

First, it was perform a multiple sequence alignment with **FeatureData[Sequence]** to create a **FeatureData[AlignedSequence]** QIIME 2 artifact. Tree construction though optional, may be useful for computing *alpha diversity metrics* that are phylogenetically based. 

The resulting tree is unrooted and is created using Fasttree. Since some downstream steps will require a rooted tree, used the longest branch to root the tree (i.e. *midrooting*).

```bash
qiime alignment mafft \
--i-sequences rep-seqs.qza \
--o-alignment aligned-rep-seqs.qza
```

Then was mask (or filter) the alignment to remove positions that are highly variable. These positions are generally considered to add noise to a resulting phylogenetic tree.


#### mask (or filter) the alignment to remove positions that are highly variable

```bash
qiime alignment mask \
--i-alignment aligned-rep-seqs.qza \
--o-masked-alignment masked-aligned-rep-seqs.qza
```

### FastTree to generate a phylogenetic tree from the masked alignment

Next, it was apply FastTree to generate a phylogenetic tree from the masked alignment file (`masked-aligned-rep-seqs.qza`).

```bash
qiime phylogeny fasttree \
--i-alignment masked-aligned-rep-seqs.qza \
--o-tree unrooted-tree.qza
```

The FastTree program creates an unrooted tree, however, it is necessary that a middle-point of rooting be applied as the mid-point of greatest distance from a branch-tip of another nonrooted tree.


```bash
qiime phylogeny midpoint-root \
--i-tree unrooted-tree.qza \
--o-rooted-tree rooted-tree.qza
```

## Obtaining and importing reference data sets (16S only with 99% OTU used)

Taxonomic classifiers perform best when they are trained based on your specific sample preparation and sequencing parameters. Two elements are required for training the classifier: the reference sequences and the corresponding taxonomic classifications. The information was used in the analysis of the SILVA database (v.128) designed for use with QIIME-compatible. Using the file containing the same as the 7 levels, but uses the 90% majority taxonomy.


#### Training feature classifiers

```bash
qiime tools import \
--type 'FeatureData[Sequence]' \
--input-path 99_otus_16S.fasta \
--output-path 99_otus.qza
```

```bash
qiime tools import \
--type 'FeatureData[Taxonomy]' \
--source-format HeaderlessTSVTaxonomyFormat \
--input-path majority_taxonomy_7_levels.txt \
--output-path ref-taxonomy.qza
```

It was provide a Silva-based 16S classifiers to carry out the taxonomic analysis the following. And after obtaining the taxonomic data of the SILVA, a *taxonomic classification of features* using a variety of Naive Bayes methods was done to make the taxonomical classification file that will be used to identify the OTUs present in the samples.


#### Train the classifier, using the reference reads and taxonomy that we just created

```bash
qiime feature-classifier extract-reads \
--i-sequences 99_otus.qza \
--p-f-primer CCTA.....CAG \
--p-r-primer GAC......TCC \
--o-reads ref-seqs.qza
```

```bash
qiime feature-classifier fit-classifier-naive-bayes \
--i-reference-reads ref-seqs.qza \
--i-reference-taxonomy ref-taxonomy.qza \
--o-classifier classifier.qza
```

___

# Taxonomic analysis (OTU)


## Assigning taxonomy to the OTU table

As previously mentioned this classifier was pretrained on Silva 16S database with 99% OTUs. It was apply this classifier to sequences, and was generate a visualization of the resulting mapping from sequence to taxonomy.

```bash
qiime feature-classifier classify-sklearn \
--i-classifier classifier.qza \
--i-reads rep-seqs.qza \
--o-classification taxonomy.qza
```

```bash
qiime metadata tabulate \
--m-input-file taxonomy.qza \
--o-visualization taxonomy.qzv
```

Next, it was can view of the classified sequences with interactive bar plots.

\newpage

to be continued...



\newpage

# Alpha and Beta diversity

## Alpha rarefaction

It was alpha diversity as a function of sampling depth using the `qiime diversity alpha-rarefaction` visualizer. Average diversity values will be plotted for each sample at each even sampling depth, and samples can be grouped based on metadata. The value provided for `--p-max-depth` was determined by reviewing the *"Frequency per sample"* information presented in the `table.qzv` file created above.

In general, choosing a value that is around the median frequency seems to work well, but you may want to increase that value if the lines in the resulting rarefaction plot do not appear to be leveling out, or decrease that value if you seem to be losing many of your samples due to low total frequencies closer to the minimum sampling depth than the maximum sampling depth.

```bash
qiime diversity alpha-rarefaction \
--i-table table.qza \
--i-phylogeny rooted-tree.qza \
--p-max-depth 12000 \
--m-metadata-file sample-metadata.tsv \
--o-visualization alpha-rarefaction.qzv
```

The *alpha diversity metrics* it is important for understanding that certain metrics are stricly qualitative (presence/absence), that is they only take diversity into account, often referred to as *richness* of the community (e.g. observed otus). 

In contrast, other methods are quantitative in that they consider both richness and abundance across samples, commonly referred to as evenness (e.g. Shannon). Yet other methods take phylogenetic distance into account by asking how diverse the phylogenetic tree is for each sample. These phylogenetic tree-based methods include the popular Faith’s PD, which calculates the sum of the branch length covered by a sample.

<center>
![Alpha Rarefaction](~/Desktop/Results_v4/fig_report/alpha\ rarefaction_View_16S.png)
![](~/Desktop/Results_v4/fig_report/version2_figs/alpha rarefaction_leg_View.png){width=15%}
</center>

Produce two plots that shows the impact of rarefaction (sampling at different depths) on alpha diversity of each sample. These are also called *‘collectors curves’*. 

The top plot is an alpha rarefaction plot, and is primarily used to determine if the richness of the samples has been fully observed or sequenced. If the lines in the plot appear to *“level out”* (i.e., approach a slope of zero) at some sampling depth along the x-axis. But, if the lines in the plot don’t level out, this may be because the richness of the samples hasn’t been fully observed yet (because too few sequences were collected), or it could be an indicator that a lot of sequencing error remains in the data (which is being mistaken for novel diversity). 

The bottom plot in this visualization is important when grouping samples by metadata. It illustrates the number of samples that remain in each group when the feature table is rarefied to each sampling depth.

In this analysis, among the group of patients the curves are very close to each other by Shanon's measure trying to remain stable along the x-axis. The control in turn tends to have reduced the number Shanon value as well as a drop in the sample number as *Sequencing Depth*.
