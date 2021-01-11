# FAIRFAX MONOCYTE_TWAS
TWAS weights were computed from four monocyte cell strains.

Monocyte expression data was downloaded from array express (https://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-2232/).  The corresponding genetic data was obtained from Dr Julian Knight University of Oxford under Licence  (Fairfax et al., 2012, 2014, Naranbhai et al., 2015a, b) 


Expression data from naïve and induced monocytes. 

Fairfax et al exposed primary CD14+ human monocytes from 432 European volunteers to the inflammatory proxies interferon-γ (IFN-γ) or differing durations (2 or 24 hours) of lipopolysaccharide (LPS).

1. naïve (CD14+): 414 individuals
2. exposed to IFN gamma:24h: 367 individuals
3. exposed to Lipopolysaccharide: 2h : 322 individuals
4. exposed to Lipopolysaccharide: 24h : 322 individuals

Data was available from 228 individuals for all four conditions:

#################################

COMPUTING TWAS weights

The TWAS weights were computed with data for the 228 individuals.

Array express files:

Investigation description	E-MTAB-2232.idf.txt
Sample and data relationship	E-MTAB-2232.sdrf.txt
Raw data (2)	E-MTAB-2232.raw.1.zip, E-MTAB-2232.raw.2.zip
Processed data (2)	E-MTAB-2232.processed.1.zip, E-MTAB-2232.processed.2.zip
Array design	A-MEXP-2210.adf.txt


Monocyte expression data

We extracted the Array_Address_Ids  of the filtered probe set (15,421 probes) from the Fairfax et al Supplementary Materials (https://science.sciencemag.org/content/suppl/2014/03/05/343.6175.1246949.DC1?_ga=2.250430726.142617004.1580743814-1392779675.1580743814) file: 1246949stableS1.xlsx. An in-house python script was used to convert Array_Address_Ids to Illumina Probe ids using the annotation information for the Illumina HumanHT-12_V4_0_R1_15002873_B array, downloaded from 
https://www.ebi.ac.uk/arrayexpress/files/A-MEXP-2210/A-MEXP-2210.adf.txt and 
probes that mapped to single genes for the 228 individuals with matched expression data available across all four cell states (naiive CD14+ and CD14+ induced with LPS2, LPS 24 or IFN-γ) were extracted (12469 probes, mapping to 9743 genes). Probes were mapped to human genome assembly GRCh37 (hg19) using the annotation information for the illumina_humanht_12_v4 chip in R using the Biomart package (Durinck et al. 2005, 2009)  and collapsed to genes using the collapseRows function from the WGCA package (Langfelder and Horvath 2008) using the MaxMean method (Miller et al. 2011) in R.

Monocyte genetic data

Genetic data files were aligned to the human genome assembly hg19 using the Liftover tool: https://genome.ucsc.edu/cgi-bin/hgLiftOver was used to convert the SNP co-ordinates to the hg19 genome assembly. Plink 1.9 http://www.cog-genomics.org/plink/1.9/ was used for standard Quality-Control analysis (Anderson et al., 2010). Genetic data for the 228 individuals with matched expression data across all four cell states was extracted and SNPs were removed if their minor allele frequency (MAF) < 0.01, missingness of genotypes ≥ 0.02 or HWE < 10−6.  A total of 625793 variants were retained for 228 people.

Expression weights
Expression weights for the monocyte data  were computed using the R script :  FUSION.compute_weights.R  from the FUSION software (Gusev et al., 2016), using the binary plink files  for the 228 individuals with matched expression data across all four cell strains and the corresponding expression data for each cell strain. Weights were packaged using the script from Oliver Pain (OP_packaging_fusion_weights.R : https://github.com/opain/Calculating-FUSION-TWAS-weights-pipeline.). GTEx7 and CMC expression weights and the reference panel from the 1000 Genomes European population were downloaded from the FUSION web site . 


Nunber of genes the expression weights:

Fairfax_CD14_QC:
number of RDat files = 1668
Fairfax_LPS2_QC:
number of RDat files = 1559
Fairfax_LPS24_QC
number of RDat files = 1579
Fairfax_IFN_QC
number of RDat files = 1807


# CTS (Cardiogenics Transcriptomic Study) CD14+ MONOCYTE TWAS WEIGHTS

We computed TWAS weights using an independent monocyte expression data set from the Cardiogenics Transcriptomic Study (CTS) (Garnier et al., 2013). In this study, CD14+ monocytes were purified from 758 individuals (459 patients with coronary artery disease or myocardial infarction and 458 healthy individuals). We used matched genetic and expression data from this study from all 758 individuals to compute an independent set of CD14+ monocyte expression weights. 3163 genes were modelled with significant cis - heritable expression. 


We used quality controlled CTS monocyte expression data : file EGAF00000183279/monocyte_expression_subset.txt. (Garnier et al., 2013) We extracted 
20, 356 autosomal single gene probes and mapped them to the GRCh37 (hg19) genome assembly using the illumina_humanref_8_v3 annotation information using the Biomart package in R (URL.5), expression probes for were collapsed to  15, 344 genes using the 'collapseRows' function from the WGCA package (URL.6) using the MaxMean method (Miller et al., 2011) in R. Genetic data files Cardiogenics (CTS) data sets were aligned to the GRCh37 (hg19) using the Liftover tool (URL.7). Plink 1.9 (URL.8) was used for standard Quality-Control analysis (Anderson et al., 2010). Genetic data for all 758 individuals from the CTS study was used. SNPs were removed if their minor allele frequency (MAF) < 0.01, missingness of genotypes ≥ 0.02 or Hardy Weinberg equilibrium (HWE) < 10−6. For the CTS study, a total of 509, 870 SNPs were retained for 758 people.
Expression weights were computed using the Fusion software, as for teh Fairfax data above.


References

Anderson CA, Pettersson FH, Clarke GM, Cardon LR, Morris AP, Zondervan KT. Data quality control in genetic case-control association studies. Nat Protoc 2010; 5: 1564–1573.

Fairfax BP, Humburg P, Makino S, Naranbhai V, Wong D, Lau E, Jostins L, Plant K, Andrews R, McGee C, et al. 2014. Innate Immune Activity Conditions the Effect of Regulatory Variants upon Monocyte Gene Expression. Science (80- ) 343: 1246949–1246949. http://www.ncbi.nlm.nih.gov/pubmed/24604202 

Fairfax BP, Makino S, Radhakrishnan J, Plant K, Leslie S, Dilthey A, Ellis P, Langford C, Vannberg FO, Knight JC. 2012. Genetics of gene expression in primary immune cells identifies cell type-specific master regulators and roles of HLA alleles. Nat Genet 44: 502–10. http://www.ncbi.nlm.nih.gov/pubmed/22446964 .

Garnier S, Truong V, Brocheton J, Zeller T, Rovital M, Wild PS, et al. Genome-Wide Haplotype Analysis of Cis Expression Quantitative Trait Loci in Monocytes. PLoS Genet 2013; 9: e1003240.

Gusev A, Ko A, Shi H, Bhatia G, Chung W, Penninx BWJH, et al. Integrative approaches for large-scale transcriptome-wide association studies. Nat Genet 2016; 48: 245–52.

Naranbhai V, Fairfax BP, Makino S, Humburg P, Wong D, Ng E, et al. Genomic modulators of gene expression in human neutrophils. Nat Commun 2015; 6: 7545.

Naranbhai V, Fletcher HA, Tanner R, O’Shea MK, McShane H, Fairfax BP, et al. Distinct Transcriptional and Anti-Mycobacterial Profiles of Peripheral Blood Monocytes Dependent on the Ratio of Monocytes: Lymphocytes. EBioMedicine 2015; 2: 1619–1626.
