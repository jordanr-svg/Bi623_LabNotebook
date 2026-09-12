

#     PS7 Part 2

Also PS1 in Bi623

## 08/27/2026

1. Completed pseudocode "Part2/ParsePseudocode.md" and started writing args and started making first best hits dictionaries
2. Made test files for edge cases where:
   - both query and subject id are the same (keep first read)
   - query id and evalue are the same -> don't keep
       - but if you remove from dictionary the next item with that query id will be add so make a flag in dictionary


## 08/29/2026

1. Test file swap with: Pen, Hannah B., and Diya

## 08/31/2026

1. Made it to populating the reciprocal best hits dictionary (double check logic)
2. Wrote biomart dictionary
3. started formating output code


## 09/01/2026

1. Sorted input files with sbatch script
sbatch script: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/sort.sh
slurm out: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/slurm...
2. Ran sorted scrips for reciprocal hits through sbatch

sbatch script: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/reciprocal_hits.sh

slurm out: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/slurm...

3. My code is outputting the wrong read counts, after trouble shooting and making it worse (at times getting 6 reads or 16,000) I will revisit in the morning and ask for help since I haven't made progress in ~3 hours


## 09/02/2026

1. Leslie helped me edit my sort script and reciprocal best hits dictionaries which was never entering its second if statement because of bad syntax.
2. New sorted slurm out script: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/slurm-47032195.out
3. New rbh slurm out: /projects/bgmp/jordanro/bioinfo/Bi621/PS/jordanr-svg-Bi621-PS7/Part2/slurm-47032264.out
4. Still getting wrong counts with the sorted files, I tried running ome of the unsorted files through my rbh code and got the right read count for reciprocal hits
5. Final slurm for reciprocal best hits with unsorted files:

	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Hsa_query_Dre_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Dre_query_Hsa_db.txt -t Dre_biomart_v116.txt -b Hsa_biomart_v116.txt -o outDre_Hsa_recip.txt"
	User time (seconds): 5.05
	System time (seconds): 0.34
	Percent of CPU this job got: 95%
	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Hsa_query_Eel_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Eel_query_Hsa_db.txt -t Hsa_biomart_v116.txt -b Eel_biomart_v116.txt -o outHsa_Eel_recip.txt"
	User time (seconds): 3.03
	System time (seconds): 0.20
	Percent of CPU this job got: 95%
	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Hsa_query_Pka_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Pka_query_Hsa_db.txt -t Hsa_biomart_v116.txt -b Pka_biomart_v116.txt -o outHsa_Pka_recip.txt"
	User time (seconds): 3.23
	System time (seconds): 0.25
	Percent of CPU this job got: 96%
	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Dre_query_Eel_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Eel_query_Dre_db.txt -t Dre_biomart_v116.txt -b Eel_biomart_v116.txt -o outDre_Eel_recip.txt"
	User time (seconds): 3.38
	System time (seconds): 0.26
	Percent of CPU this job got: 97%
	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Dre_query_Pka_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Pka_query_Dre_db.txt -t Dre_biomart_v116.txt -b Pka_biomart_v116.txt -o outDre_Pka_recip.txt"
	User time (seconds): 3.82
	System time (seconds): 0.27
	Percent of CPU this job got: 97%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:04.19
	Command being timed: "./parse.py -i /projects/bgmp/shared/Bi623/PS1/blasthits/Eel_query_Pka_db.txt -f /projects/bgmp/shared/Bi623/PS1/blasthits/Pka_query_Eel_db.txt -t Pka_biomart_v116.txt -b Eel_biomart_v116.txt -o outEel_Pka_recip.txt"
	User time (seconds): 2.31
	System time (seconds): 0.16
	Percent of CPU this job got: 95%

SOMETHING IS STILL WRONG WITH MY CODE: I should be able to run sorted files though it and get the same number of reads, It works on unsorted files but not sorted -> I don't have time to figure out why but maybe next week I will see what is happening with my code.