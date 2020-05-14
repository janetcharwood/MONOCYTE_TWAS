# MONOCYTE_TWAS
TWAS weights computed from four monocyte cell strains
Monocyte expression weights were computed using the genetic and expression data and from Fairfax et al 2014. 


FAIRFAX DATA files: expression data from naïve and induced monocytes. 
Fairfax et al exposed primary CD14+ human monocytes from 432 European volunteers to the inflammatory proxies interferon-γ (IFN-γ) or differing durations (2 or 24 hours) of lipopolysaccharide (LPS) (Fairfax et al. 2014)

1. naïve (CD14+): 414 individuals
2. exposed to IFN gamma:24h: 367 individuals
3. exposed to Lipopolysaccharide: 2h : 322 individuals
4. exposed to Lipopolysaccharide: 24h : 322 individuals

Data was available from 228 individuals for all four conditions:

#################################


COMPUTING TWAS weights


The TWAS weights were computed with data for the 228 individuals.

Expression data was downloaded from array express (https://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-2232/). 

files:

Investigation description	E-MTAB-2232.idf.txt
Sample and data relationship	E-MTAB-2232.sdrf.txt
Raw data (2)	E-MTAB-2232.raw.1.zip, E-MTAB-2232.raw.2.zip
Processed data (2)	E-MTAB-2232.processed.1.zip, E-MTAB-2232.processed.2.zip
Array design	A-MEXP-2210.adf.txt



We received the corresponding genetic data from Dr Julian Knight University of Oxford under Licence  (Fairfax et al. 2012, 2014; Naranbhai et al. 2015b, 2015a) 


Monocyte expression data

Fairfax et al exposed primary CD14+ human monocytes from 432 European volunteers to the interferon-γ (IFN-γ) or lipopolysaccharide (LPS) for 2 or 24 hours  (Fairfax et al. 2014) . We extracted the Array_Address_Ids  of the filtered probe set (15,421 probes) from the Fairfax et al Supplementary Materials (https://science.sciencemag.org/content/suppl/2014/03/05/343.6175.1246949.DC1?_ga=2.250430726.142617004.1580743814-1392779675.1580743814) file: 1246949stableS1.xlsx. An in-house python script was used to convert Array_Address_Ids to Illumina Probe ids using the annotation information for the Illumina HumanHT-12_V4_0_R1_15002873_B array, downloaded from 
https://www.ebi.ac.uk/arrayexpress/files/A-MEXP-2210/A-MEXP-2210.adf.txt and 
probes that mapped to single genes for the 228 individuals with matched expression data available across all four cell states (naiive CD14+ and CD14+ induced with LPS2, LPS 24 or IFN-γ) were extracted (12469 probes, mapping to 9743 genes). Probes were mapped to human genome assembly GRCh37 (hg19) using the annotation information for the illumina_humanht_12_v4 chip in R using the Biomart package (Durinck et al. 2005, 2009)  and collapsed to genes using the collapseRows function from the WGCA package (Langfelder and Horvath 2008) using the MaxMean method (Miller et al. 2011) in R.

Monocyte genetic data

Genetic data files were aligned to the human genome assembly hg19 using the Liftover tool: https://genome.ucsc.edu/cgi-bin/hgLiftOver was used to convert the SNP co-ordinates to the hg19 genome assembly. We ran SNP-QC to check the SNPs in each data set using the script HRC-1000G-check-bim-NoReadKey.pl script from McCarthy tools https://www.well.ox.ac.uk/~wrayner/tools/ and the HRC reference SNP list : v1.1 HRC.r1-1.GRCh37.wgs.mac5.sites.tab from the Haplotype Reference Consortium:
http://www.haplotype-reference-consortium.org/site. We used plink 1.9 http://www.cog-genomics.org/plink/1.9/ for all subsequent SNP- QC and data merging. After merging the two datasets the genetic data for the 228 individuals with matched expression data across all four cell states was extracted. In the final QC SNPs from 228 individuals, SNPs were removed if their minor allele frequency (MAF) < 0.01, missingness of genotypes ≥ 0.02 or HWE < 10−6.  A total of 625793 variants were retained for 228 people.

Nunber of genes the expression weights:

Fairfax_CD14_QC:
number of RDat files = 1668
Fairfax_LPS2_QC:
number of RDat files = 1559
Fairfax_LPS24_QC
number of RDat files = 1579
Fairfax_IFN_QC
number of RDat files = 1807






Fairfax BP, Humburg P, Makino S, Naranbhai V, Wong D, Lau E, Jostins L, Plant K, Andrews R, McGee C, et al. 2014. Innate Immune Activity Conditions the Effect of Regulatory Variants upon Monocyte Gene Expression. Science (80- ) 343: 1246949–1246949. http://www.ncbi.nlm.nih.gov/pubmed/24604202 


Fairfax BP, Makino S, Radhakrishnan J, Plant K, Leslie S, Dilthey A, Ellis P, Langford C, Vannberg FO, Knight JC. 2012. Genetics of gene expression in primary immune cells identifies cell type-specific master regulators and roles of HLA alleles. Nat Genet 44: 502–10. http://www.ncbi.nlm.nih.gov/pubmed/22446964 .



