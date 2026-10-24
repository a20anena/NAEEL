## PART 1 ( Retrieval)

1. AMINO ACID FOUND :  147
2. The status of Swiss-Prot is reviewed
3. I retrieved RefSeq mRNA NM_000518.5
4. GO annotations are 25
- evidence codes are follwing 
      2 HDA:
      1 HMP:
      4 IBA:
     10 IDA:
      1 IEA:
      1 IMP:
      2 NAS:
      4 TAS:

5. 348 structures of  protein(P68871) are in the Protein Data Bank.
-  Following were solved with each experimental method 
40  EM
2  Neutron
2  NMR
304  X-ray
6. 628 BASE PAIR long is mRNA, according to the GenBank record.

## Comment on distribution of its evidence codes
25 GO annotation is in  protein P68871. 14 are experimental (2 HDA, 1HMP, 10 IDA, 1 IMP). and its trust level is high. 4 IBA are similar from related protein. 1 IEA which is automatic, an trust level is low because its fully automated. 2 NAS AND 4 TAS are from statements of authors.  So the annotation is mostly based on experiments and can be trusted.
## COMMAND USED PART 1
1. grep -v ">" protein.fasta | tr -d '\n' | wc -c
2. grep "^ID" protein.txt
3. grep "^DR   RefSeq" protein.txt 
4. grep "^DR   GO;" protein.txt | grep -oE "[A-Z]{2,3}:" | sort | uniq -c
5. grep -c "^DR   PDB;" protein.txt
- grep "^DR   PDB;" protein.txt | cut -d";" -f3 | sort | uniq -c
6. grep "LOCUS" mRNA.gb


## COMMAND USED TO DOWNLOAD FILES
1.  curl "https://rest.uniprot.org/uniprotkb/P68871.fasta" \ > protein.fasta
2. curl "https://rest.uniprot.org/uniprotkb/P68871.txt" > protein.txt
3. curl "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=NM_000518.5&rettype=gb&retmode=text" > mRNA.gb
4. curl "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=NM_000518.5&rettype=fasta&retmode=text" > mRNA.fasta


## Part 2 (BLAST)

1.  job ID of your Slurm job : Submitted batch job 48116608
- 872 hits of blastp_local.txt
2. E-value and percent identity and top 3 hits 
- P68873  100.000 6.56e-106       301
- P68872  100.000 6.56e-106       301
- P68871  100.000 6.56e-106       301
3. Sorted the hits by E-value, smallest first 
- sp|P68871|HBB_HUMAN     P68871  100.000 147     0       0       1       147     1       147     6.56e-106       301
- sp|P68871|HBB_HUMAN     P68872  100.000 147     0       0       1       147     1       147     6.56e-106       301
- sp|P68871|HBB_HUMAN     P68873  100.000 147     0       0       1       147     1       147     6.56e-106       301
- sp|P68871|HBB_HUMAN     P02024  99.320  147     1       0       1       147     1       147     2.29e-105       300
- sp|P68871|HBB_HUMAN     P02025  98.630  146     2       0       2       147     1       146     3.34e-103       294

- why sort -k11 -n would not give the right order for your file. because -n does not understand e-notation. It reads 2.1e-150 as 2.1 and 1.1e-90 as 1.1, so it puts 1.1e-90 first. So I used g for E-values.  i used -k11,11 uses column 11 only.

## run the search a second time with a stricter E-value threshold

in first search i used 1e-5, and in second research i used 1e-50. in first search i got job 48116608 and in second search i got job 48117673. in first search i got 872 hits but in second search i got only 372 hits. The stricter limit removed 500 hits, which is about 57 %.
 The top hits (P68873, P68872, P68871) did not change, because they have very good E-values.

Commands:
- sbatch blastp_second.sh
- wc -l blastp_second.txt
- cut -f2,3,11,12 TP53_blastp_local.txt | head -5
 
## COMMAND USED PART 2  
1. sbatch blast.sh
- wc -l blastp_local.txt
2. cut -f2,3,11,12 blastp_local.txt | head -3
3. sort -t$'\t' -k11,11g blastp_local.txt | head -5




