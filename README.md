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



## COMMAND USED PART 1
1. grep -v ">" protein.fasta | tr -d '\n' | wc -c
2. grep "^ID" protein.txt
3. grep "^DR   RefSeq" protein.txt 
4. grep "^DR   GO;" protein.txt | grep -oE "[A-Z]{2,3}:" | sort | uniq -c













## COMMAND USED TO DOWNLOAD FILES
1.  curl "https://rest.uniprot.org/uniprotkb/P68871.fasta" \
> protein.fasta
2. curl "https://rest.uniprot.org/uniprotkb/P68871.txt" > protein.txt
3. 
