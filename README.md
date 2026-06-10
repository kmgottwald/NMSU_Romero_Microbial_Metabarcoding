Processing DNA-seq of soil README
Protocol for processing microbial amplicon sequences (16S & ITS) from dryland soils
Sequencing data (demultiplexed fastq files) is available on NCBI's SRA database:  PRJNA1471992
I followed DADA2 Pipeline Tutorial (1.16) & (1.8) to process 16S & ITS sequences respectively
This pipeline is divided into 7 sections. Each section has a filename and step.
Codes are bash script, work was conducted in NMSU high-power computing Discovery cluster
Section 1
File name: Cut_primers.txt
Step: Remove primers from sequences using Cutadapt (version 5.1)
Notes: Primers were specified by SeqCoast Genomics. The files on SRA are primer-trimmed, so skip this step if using that data.
Section 2
File name: Fastqc_Multiqc_Report.txt
Step: Generate QC reports for each fastq file and the dataset as a whole
Section 3
File name: dada2_qualitycheck.txt
Step: Visualize read quality using Dada2
Notes: From this point on, work was conducted in an R environment through HPC, so scripts are a mix of bash and R.
Section 4
File names: dada2_trim_16s.txt & dada2_trim_ITS.txt
Step: Trim & filter sequences based on previous step to retain good quality data and get rid of bad quality data
Section 5
File name: dada2_error_rates.txt
Step: Visualize error rates from previous step
Section 6
File name: dada2_merge_ASV.txt
Step: Merge forward and reverse reads, generate ASV table, assign taxonomy
Section 7
File name: Decontam.txt
Step: Remove contaminants from ASV tables using R package "decontam" and sequences from negative control (blank)
Notes: The blank sequences are also available in SRA, sample name is 6509_202.
