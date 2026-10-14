# Mouse H3K4me3 ChIP-seq Analysis

## Project Overview

This project demonstrates a ChIP-seq analysis workflow to investigate the genomic distribution of **H3K4me3**, a histone modification commonly associated with active gene promoters, in mouse samples.

The workflow covers read quality assessment, adapter/quality trimming, reference genome alignment, peak calling, signal-track generation, peak annotation, and Gene Ontology (GO) Biological Process enrichment analysis.

This is an educational bioinformatics portfolio project using a small, shallow sequencing dataset.

## Dataset

- **SRA Study:** [SRP000202](https://www.ncbi.nlm.nih.gov/sra/?term=SRP000202)
- **ChIP sample:** SRR001586 — Mouse H3K4me3 ChIP
- **Input control:** SRR001591 — Mouse Input
- **Reference genome:** Mouse GRCm39
- **Reference accession:** GCF_000001635.27
- **Read type:** Single-end sequencing

## Tools Used

| Tool | Purpose |
|---|---|
| FastQC | Read quality assessment before and after trimming |
| fastp | Read quality control and trimming |
| Bowtie2 | Alignment to the mouse reference genome |
| SAMtools | SAM/BAM processing, sorting, indexing, and alignment statistics |
| MACS3 | Broad peak calling using ChIP and Input samples |
| deepTools | Normalized BigWig signal-track generation |
| IGV | Visual inspection of genomic signal tracks and peaks |
| R and RStudio | Downstream analysis and visualization |
| ChIPseeker | Peak annotation and TSS-distance analysis |
| clusterProfiler | GO Biological Process enrichment |
| org.Mm.eg.db | Mouse gene annotation for enrichment analysis |

## Workflow

1. **Quality assessment:** Evaluated raw sequencing reads using FastQC.
2. **Read trimming:** Used fastp to trim reads and assessed the trimmed reads with FastQC.
3. **Read alignment:** Aligned ChIP and Input reads to the GRCm39 reference genome using Bowtie2.
4. **BAM processing:** Converted SAM files to BAM, sorted and indexed the alignments, and assessed alignment statistics using SAMtools.
5. **Peak calling:** Used MACS3 in broad-peak mode with the Input control and a no-model approach.
6. **Signal generation:** Generated CPM-normalized BigWig tracks using deepTools.
7. **Genome visualization:** Inspected the signal tracks and called peaks in IGV.
8. **Peak annotation:** Used ChIPseeker with a mouse GRCm39 annotation database to annotate peaks and examine their distances from transcription start sites (TSSs).
9. **Functional enrichment:** Performed GO Biological Process enrichment using clusterProfiler and the mouse annotation database.

## Key Results

- ChIP alignment rate: approximately **98.23%**.
- Input alignment rate: approximately **98.28%**.
- MACS3 identified **105 broad-peak regions** in the selected analysis.
- Peak annotation classified 104 peaks within 1 kb of a promoter and one peak within 1–2 kb of a promoter.
- The annotation analysis identified **74 unique associated genes**.
- Of these, **63 genes were mapped** for GO enrichment analysis.
- GO Biological Process enrichment returned exploratory themes involving synaptic/postsynaptic structure, endocytosis and endosomal transport, reactive oxygen species metabolism, interferon response, and nucleotide metabolism.
- No GO Biological Process terms passed the conventional Benjamini–Hochberg adjusted p-value threshold of 0.05.

These enrichment themes are exploratory and should not be interpreted as statistically significant biological conclusions.

## Visualizations

### 1. Peak Annotation Distribution

This pie chart summarizes the genomic annotation of the called H3K4me3 peaks, highlighting their distribution across annotated genomic regions.

![Peak Annotation Pie Chart](Results/Plots/ChIPseq_Peak_Annotation_Pie.png)

### 2. Peak Annotation by Genomic Region

This bar chart compares the genomic annotation categories associated with the called peaks.

![Peak Annotation Bar Chart](Results/Plots/ChIPseq_Peak_Annotation_Bar.png)

### 3. Peak Distance from Transcription Start Sites (TSS)

This plot illustrates the distribution of distances between the called peaks and transcription start sites (TSS), helping assess their proximity to gene promoters.

![TSS Distance Plot](Results/Plots/ChIPseq_TSS_Distance_Plot.png)

## Outputs

The project includes selected outputs such as:

- FastQC HTML reports before and after trimming
- MACS3 broadPeak, gappedPeak, and peak report files
- CPM-normalized BigWig signal tracks
- SAMtools alignment statistics
- Peak annotation and annotation summary tables
- TSS-distance, annotation pie, and annotation bar plots
- Associated gene list
- Complete GO Biological Process enrichment results
- IGV session file for visualization

## Limitations

- This project uses one ChIP sample and one Input control.
- The dataset has shallow sequencing depth and short reads, limiting biological interpretation.
- The peak calls and associated gene list should be treated as exploratory.
- The analysis does not establish that the associated genes are differentially expressed or that H3K4me3 directly regulates their expression.
- GO enrichment results did not meet the adjusted p-value significance threshold.

The project is intended to demonstrate a bioinformatics workflow and interpretation of results, not to provide publication-grade conclusions.

## Skills Demonstrated

- NGS quality control and trimming
- Reference-based sequence alignment
- SAM/BAM processing and quality assessment
- ChIP-seq peak calling
- Genome-browser visualization
- Peak annotation and TSS-distance analysis
- GO enrichment analysis and multiple-testing correction
- Result interpretation and scientific reporting

## Environment

- **Operating System:** Windows 11 with WSL (Ubuntu)
- **Conda Environment:** `trimming_env` — fastp, SRA Toolkit, Bowtie2, and SAMtools
- **Conda Environment:** `chipseq_env` — MACS3 and deepTools
- **R Environment:** Windows R 4.6.0 and RStudio
- **R/Bioconductor Packages:** ChIPseeker, clusterProfiler, and org.Mm.eg.db
- **FastQC:** Installed separately on Windows
- **Genome Browser:** IGV with Java 21
- **Reference Genome:** Mouse GRCm39

## Acknowledgements

- Raw sequencing data were obtained from the NCBI Sequence Read Archive (SRA), Study **SRP000202**.
- **ChIP sample:** SRR001586 — Mouse H3K4me3 ChIP.
- **Input control:** SRR001591 — Mouse Input.
- The mouse reference genome was obtained from NCBI RefSeq: **GCF_000001635.27 (GRCm39)**.
- The sequencing data and reference genome are publicly available through the National Center for Biotechnology Information (NCBI).

## Author

**Manishkumar R**  
M.Sc. Biotechnology  
Chennai, Tamil Nadu, India  

Email: [rmanishkumar1702@gmail.com](mailto:rmanishkumar1702@gmail.com)  
GitHub: [rmanishkumar1702-DESK](https://github.com/rmanishkumar1702-DESK)


This project is licensed under the MIT License. See the `LICENSE` file for details.
