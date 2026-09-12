# Bi623 Project 2: Electric organ RNA-seq analysis

## Parts 1-3:

### 08/27/2026:

- Project 2 assigned
- ran pixi init to installed 

    ✔ Added fastqc >=0.12.1,<0.13

    ✔ Added cutadapt >=5.2,<6

    ✔ Added trimmomatic >=0.41,<0.42

- Used sbatch to run prefetch for SRR25630312 and SRR25630410 from SRA than ran fasterq dump for each. All sbatch scripts and outputs are in the folder: /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/bash_scripts
- Ran fastqc using sbatch script in sam bash_scripts/ folder. 
     - code: /usr/bin/time -v pixi run fastqc *.fastq
     - Output Files Folder: fastqc_htmls/
- finished fastqc report and uploaded to github repo.

### 09/02/2026:
- ran cutadapt for both files, ran both in one sbatch shell script Project2_Part2/cutadapt.sh

- example of word count (for one line) length change after cutadapt

    $head -3 /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/bash_scripts/SRR25630410_1.fastq | tail -2 /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/bash_scripts/SRR25630410_1.fastq | wc -c
    Returned: 224
    AFTER CUTADAPT
    $head -3 /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/cutAdaptout0410.1.fastq | tail -2 /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/cutAdaptout0410.1.fastq | wc -c
    Returned: 153

    - running trimmomatic with sbatch script: Project2_Part2/trimming.sh

    - plotted trimmed read distribution using rstudio

    file: /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/Project2_Part2_answers.R

    - distribution graphs in file: Project2_Part2/read_distribution_graphs


- Downloaded files for part 3:

✔ Added star >=2.7.11b,<3

✔ Added samtools >=1.23.1,<2

✔ Added numpy >=2.5.2,<3

✔ Added matplotlib >=3.11.1,<4

✔ Added htseq >=2.1.2,<3

### 09/03/2026:
- Made reference database with files:

/projects/bgmp/shared/Bi623/Project2/campylomormyrus.fasta

- projects/bgmp/shared/Bi623/Project2/campylomormyrus.gff

- sbatch script: make_dbCam.sh
- slurm output:
 WARN cache for Repodata at /home/jordanro/.cache/rattler/cache/repodata is on a network/parallel filesystem (NFS/SMB/FUSE/BeeGFS/Lustre/GPFS/CephFS), redirected to /tmp/pixi-cache-jordanro/repodata for this run. Set [cache.repodata] in config.toml or PIXI_CACHE_DIR to override, or [cache.netfs-redirect] = "never" to keep the original path.
	/gpfs/projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/.pixi/envs/default/bin/STAR-avx2 --runThreadN 8 --runMode genomeGenerate --genomeDir cam --genomeFastaFiles cam/campylomormyrus.fasta --sjdbGTFfile cam/campylomormyrus.gff
	STAR version: 2.7.11b   compiled: 2025-11-14T12:06:42+0000 :/opt/conda/conda-bld/star_1763121846936/work/source
Sep 03 10:14:04 ..... started STAR run
Sep 03 10:14:04 ... starting to generate Genome files
Sep 03 10:14:12 ..... processing annotations GTF
!!!!! WARNING: --genomeSAindexNbases 14 is too large for the genome size=862592683, which may cause seg-fault at the mapping step. Re-run genome generation with recommended --genomeSAindexNbases 13
Sep 03 10:14:17 ... starting to sort Suffix Array. This may take a long time...
Sep 03 10:14:20 ... sorting Suffix Array chunks and saving them to disk...
Sep 03 10:16:22 ... loading chunks from disk, packing SA...
Sep 03 10:16:38 ... finished generating suffix array
Sep 03 10:16:38 ... generating Suffix Array index
Sep 03 10:18:39 ... completed Suffix Array index
Sep 03 10:18:39 ... writing Genome to disk ...
Sep 03 10:18:40 ... writing Suffix Array to disk ...
Sep 03 10:18:48 ... writing SAindex to disk
Sep 03 10:18:48 ..... finished successfully
	Command being timed: "pixi run STAR --runThreadN 8 --runMode genomeGenerate --genomeDir cam --genomeFastaFiles cam/campylomormyrus.fasta --sjdbGTFfile cam/campylomormyrus.gff"
	User time (seconds): 978.56
	System time (seconds): 7.86
	Percent of CPU this job got: 344%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 4:46.65


- Aligned SRR25630312 reads to c. compressirostris database
  - slurm out:
   WARN cache for Repodata at /home/jordanro/.cache/rattler/cache/repodata is on a network/parallel filesystem (NFS/SMB/FUSE/BeeGFS/Lustre/GPFS/CephFS), redirected to /tmp/pixi-cache-jordanro/repodata for this run. Set [cache.repodata] in config.toml or PIXI_CACHE_DIR to override, or [cache.netfs-redirect] = "never" to keep the original path.
	/gpfs/projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/.
    
    pixi/envs/default/bin/STAR-avx2 --runThreadN 8 --runMode alignReads --outFilterMultimapNmax 3 --outSAMunmapped Within KeepPairs --alignIntronMax 1000000 --alignMatesGapMax 1000000 --readFilesCommand zcat --readFilesIn /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0312output_forward_paired.fq.gz /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0312output_reverse_paired.fq.gz --genomeDir cam --outFileNamePrefix EO_0312_aligned

	STAR version: 2.7.11b   compiled: 2025-11-14T12:06:42+0000 :/opt/conda/conda-bld/star_1763121846936/work/source

Sep 03 10:32:53 ..... started STAR run

Sep 03 10:32:53 ..... loading genome

Sep 03 10:32:59 ..... started mapping

Sep 03 10:43:24 ..... finished mapping

Sep 03 10:43:26 ..... finished successfully

	Command being timed: "pixi run STAR --runThreadN 8 --runMode alignReads --outFilterMultimapNmax 3 --outSAMunmapped Within KeepPairs --alignIntronMax 1000000 --alignMatesGapMax 1000000 --readFilesCommand zcat --readFilesIn /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/
    Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0312output_forward_paired.fq.gz /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0312output_reverse_paired.fq.gz --genomeDir cam --outFileNamePrefix EO_0312_aligned"

	User time (seconds): 4889.66

	System time (seconds): 25.70

	Percent of CPU this job got: 776%

	Elapsed (wall clock) time (h:mm:ss or m:ss): 10:33.12




- Aligned SRR25630410 reads to c. compressirostris database
  - slurm out:

   WARN cache for Repodata at /home/jordanro/.cache/rattler/cache/repodata is on a network/parallel filesystem (NFS/SMB/FUSE/BeeGFS/Lustre/GPFS/CephFS), redirected to /tmp/pixi-cache-jordanro/repodata for this run. Set [cache.repodata] in config.toml or PIXI_CACHE_DIR to override, or [cache.netfs-redirect] = "never" to keep the original path.
	/gpfs/projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/.pixi/envs/default/bin/STAR-avx2 --runThreadN 8 --runMode alignReads --outFilterMultimapNmax 3 --outSAMunmapped Within KeepPairs --alignIntronMax 1000000 --alignMatesGapMax 1000000 --readFilesCommand zcat --readFilesIn /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0410output_forward_paired.fq.gz /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0410output_reverse_paired.fq.gz --genomeDir cam --outFileNamePrefix EO_0410_aligned
	STAR version: 2.7.11b   compiled: 2025-11-14T12:06:42+0000 :/opt/conda/conda-bld/star_1763121846936/work/source
    
Sep 03 10:33:43 ..... started STAR run

Sep 03 10:33:43 ..... loading genome

Sep 03 10:33:48 ..... started mapping

Sep 03 10:48:06 ..... finished mapping

Sep 03 10:48:07 ..... finished successfully

	Command being timed: "pixi run STAR --runThreadN 8 --runMode alignReads --outFilterMultimapNmax 3 --outSAMunmapped Within KeepPairs --alignIntronMax 1000000 --alignMatesGapMax 1000000 --readFilesCommand zcat --readFilesIn /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0410output_forward_paired.fq.gz /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part2/SRR0410output_reverse_paired.fq.gz --genomeDir cam 
    
    --outFileNamePrefix EO_0410_aligned"

	User time (seconds): 6716.04

	System time (seconds): 31.03

	Percent of CPU this job got: 780%

	Elapsed (wall clock) time (h:mm:ss or m:ss): 14:24.81

Slurm out for stranded=yes htseq for SRR25630410

    	Command being timed: "pixi run htseq-count -i Parent --stranded=yes /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part3/EO_0410_alignedAligned.out.sam /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_Part3/cam/campylomormyrus.gff"
	User time (seconds): 2422.67
	System time (seconds): 8.13
	Percent of CPU this job got: 99%

## Part 4:

### 09/09/2026

- Completed in rstudio

- Packages:
library(tidyverse)
library(DESeq2)
library(tools)
library(limma)
library(qvalue)
library(dplyr)
library(edgeR)
library(Glimma)
library(ggplot2)
library(RColorBrewer)
library(apeglm)

- We used Deseq to compare genes that are differentially expressed in the Electric Organ and Skeletal muscle

- Workflow followed in folder: /projects/bgmp/jordanro/bioinfo/Bi623/Project2_QAA/Project-2-Electric-organ-RNA-seq-analysis/Project2_part4

file: Project2_part4-5.Rmd

other resources:
https://master.bioconductor.org/packages/release/workflows/vignettes/rnaseqGene/inst/doc/rnaseqGene.html#the-variance-stabilizing-transformation-and-the-rlog