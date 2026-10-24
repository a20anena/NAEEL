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
