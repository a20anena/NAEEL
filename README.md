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
25 GO annotation was found from the protein P68871. 4 IBA from them are Inferred from Biological aspect of Ancestor. and its trust level is  Moderate (phylogenetic inference)' 1 IMP FROM THEM IS Inferred from Mutant Phenotype, and trust level on its high. 1 IEA from them is Inferred from Electronic Annotation, an trust level is low because its fully automated, no manual review.But from all GO annotation, we found 10 IDA is Inferred from Direct Assay and its trust level is very high because its come from specific biochemical assay.           
 most GO annotations for non-model organisms are transferred computationally from model organisms based on sequence similarity. The accuracy of these transferred annotations depends on the degree of functional conservation between the organisms, which is not always high — particularly for organism-specific biological processes.

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
