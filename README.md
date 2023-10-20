# RNAseq_Overview
## RNA-Seq 
* Aim: to detect and quantify RNA moldecules within biological samples using NGS by:
** RNA/gene/transcript expression
** alternatively spliced transcripts
** gene fusion and SNPs
** post-translational modification
* RNA seq can performed by:
- total RNA (rRNA >80%)
- rRNA depleted RNA (removed rRNA)
- mRNA transcripts (performed polyA enrichment of RNA)
- small RNA (miRNA, tRNA) by selecting the size of RNA molecules
- RNA molecules transcribed at a specific time (ribosomal profiling)
- specific RNA molecules (hybridization with probes complementary to desired transcripts)
* Different techonology and protocol:
- single-end short reads (50-450 nt) - useful for gene expression quantification (Illumina)
- paired-end reads (2*50-250nt) - useful for detecting splicing events and refinement of transcriptome annotation
- single long reads (PACBio or Nanopore) - de novo identification of new transcripts and improve transcriptome assembly
* mRNA-Seq protocol (Illumina)
![image](https://github.com/JagBaskerville/RNAseq/assets/147906487/0677d146-683c-4924-b888-6df4fe3d9c0e)
- map Coding sequence with the ORF seq --> junction reads
- Exon reads --> expression profile calculated by reads
## Library preparation
* mRNA purification
mRNA is purified using polyT adapter - bind to polyA tail of RNA
--> rRNA, tRNA, long ncRNAs, miRNA, histone mRNA, degraded RNA, bacterial transcrips and viral transcripts are washed away
* RNA --> cDNA
- mRNA in RNA-Seq is 5' to 3' direction (sense RNA)
- mRNA is one-stranded --> the information of DNA strands is lost after both strands of cDNA are synthesized
- Methods: making stranded RNA-Seq libraries preserved the RNA strand information
+ Illumina's TruSeq Stranded mRNA: use dUTP instead of dTTP during the amplification --> second strand in amplification
+ Read 1(forward) is mapped to the antisense DNA strand, Read2 to sense DNA strand
* cDNA multiplexing
- Fragmented cDNA is indexed with hexamer or octamer barcode (cDNA form diff samples can be pooled into a single lane for multiplexed sequencing)
* cDNA amplification
* cDNA qualiti control and fragment selection
* Sequencing
The RNA-seq output is demultiplexed --> one fastq-file/sample (single-end reads) or 2 fastq-file/sample (paired end reads)

## Experimental design
- The important considerations could affect the quality of differential expression analysis
- 1. Number and type of replicates
  2. Avoiding confounding
  3. Addressing batch effects
  ### Replicates
  - Technical replicates and biological replicates
  + Technical replicates: repeat the exprerimental steps using the same biological sample --> measure and remove technical variation
  + Biological replicates: using diff biological samples of the same condition to measure the biological variation bw samples
  - In RNA seq, technical replicates are unneccessary but biological replicates are essential. The more biological replicates, the better estimates of biological variation and the moree precise of mean expression levels
  - More accurate modeling of data and identification of differentially expressed genes
  - Sequencing depth: total number of usable reads from the sequencing machine (usually used in the unit “number of reads” (in millions). Especially used for RNA-seq.
  - Biological replicates are greater important than seq depth: more DE genes
  - Guideline:
  + General gene-level differential expression (DE): 30 mi SE reads/samples, 15 mil reads is sufficient, if number of replicates >3
  + Gene-level DE with low-expressed gene: Seq deep at least 30-60 mil reads
  + Isoform-level DE: expression of proteins from one gene or one gene family (RNA splicing) known isoforms: at least 30 mil reads per sample and paired-end reads. Novel isoforms: >60 mil reads per samples. Perform careful QC of RNA quality
  ### Confounding
  - A coundounded RNA-seq experiment: cannot distinguish the separate effects of 2 diff sources of variation in the data
  - E.g: if all control were male and treatment are feale --> could be confounded by sex
  - To avoid:
  + Ensure animals in each condition are same sex, age, litter and batch
  + Ensure to split the animals equally bw condition
  ### Batch effects
  - Can see significant differences in expression due only to the batch effects
  - Different batch: different results due to different batch
  - Avoid:
  + Do not coundound experiment by batch
  + Do split replicates of diff sample groups across batches, more replicates is better
  + Do not include batch information in experimental metadata
