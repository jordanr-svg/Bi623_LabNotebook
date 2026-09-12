# Bi623 Project 1: Multiomics Analysis for Craniofacial Development

# Part 1
## 08/26/2026:
- Assigned part 1 and completed pseudocode to parse through gzip file and identify Regions of Continuous Constraints (ROCCs) by parsing file for Phylop scores greater than or equal to 2.27 and merging ROCCS with only one base in between.

- File: p1_test.txt -- test file

- File: Part1.py -- Started writing first part of code where I am adding ROCCs to dictionary -> I have a problem where all ROCCs are not being added to the dictionary so the problem is most likely somewhere in my if-else statements

## 09/04/2026:
    - got to my second dictionary where I merge roccs

    - planning on merging roccs and outputting to a text file, then  I will sort the text file in bash

## 09/06/2026:
    - still struggling to make progress on my merging step, talked with Robbie and Hannah S. and it seems like most people are using a list of lists not a dictionary -> might consider using strings.

## 09/07/2026:
    - Reached out to hope about my second dictionary

    - ran my python while with sbatch file: rocc.sh

        - output missing almost all roccs

    - made new test files and gzipped, also new test output files -> old test files were not tab separated

    - running my code again after bug fixing with the new test files.
        - still not getting currect output, expected output is 500,000+ and I am getting 386


# Part 2
file: Part2.R

- filtered (/projects/bgmp/shared/Bi623/ZoonomiaWorkshop/variant_summary.txt.gz) in Rstudio
    - subset for "Cranio", "Pathogenic" and "Pathogenic/Likely pathogenic", "GRCh38"
    - sorted by chromosome number than start site
    - edit chromosome to start with chr

# Part 3

## 09/09/2026

Find the epigenetics files here: /projects/bgmp/shared/Bi623/ZoonomiaWorkshop/

- GSM7508786_CS18-12676-ATAC_peaks-q1.3.narrowPeak.gz

- GSM7508787_CS18-12695-ATAC_peaks-q1.3.narrowPeak.gz

- GSM7508788_CS19-12696-ATAC_peaks-q1.3.narrowPeak.gz

- GSM7508789_CS22-12498-ATAC_peaks-q1.3.narrowPeak.gz

- GSM7508790_CS23-12492-ATAC_peaks-q1.3.narrowPeak.gz

Other files:

Craniovariants files:
/projects/bgmp/jordanro/bioinfo/Bi623/jordanr-svg-Bi623-Project-1/Cranio_variants_sorted.tsv

Rocc Output file:
/projects/bgmp/shared/Bi623/ZoonomiaWorkshop/PhyloP_RoCC_output_sorted.txt

Command used to sort each file:
sort -k 1,1 -k2,2n file > file.sorted

tail -n 225 Cranio_variants_sorted.tsv | sort -k 1,1 -k2,2n > Cranio_variants_sorted4bedtools.tsv

sort -k 1,1 -k2,2n /projects/bgmp/shared/Bi623/ZoonomiaWorkshop/PhyloP_RoCC_output_sorted.txt > PhyloP_RoCC_outputfromHope_sorted.txt

Sorted files (in part 3 folder):

GSM7508786_CS18-12676-ATAC_peaks-q1.3.narrowPeak_sorted.txt

GSM7508787_CS18-12695-ATAC_peaks-q1.3.narrowPeak_sorted.txt

GSM7508788_CS19-12696-ATAC_peaks-q1.3.narrowPeak_sorted.txt

GSM7508789_CS22-12498-ATAC_peaks-q1.3.narrowPeak_sorted.txt

GSM7508790_CS23-12492-ATAC_peaks-q1.3.narrowPeak_sorted.txt

Cranio_variants_sorted4bedtools.tsv

PhyloP_RoCC_outputfromHope_sorted.txt



# Part 4

## 09/10/2026

Plotted overlap in regions of interest.

rstudio files and output files located in jordanr-svg-Bi623-Project-1/part4/