# CG2129 — Genome-Wide Binding Profile of a Candidate TrxG Regulator

**Project type:** Research Assistant — Computational/Genomics  
**Status:** Preliminary analysis completed  
**System:** *Drosophila melanogaster* 2-3h embryos  
**Supervisor:** Dr. Muhammad Tariq, Tariq Epigenetics Lab, LUMS  
**Note:** Gene identity withheld pending publication — referred to as CG2129 throughout

---

## Biological Motivation

The Tariq Lab's genome-wide RNAi screen for Trithorax group regulators identified a number of candidate genes with TrxG-like functions. Among these, CG2129 emerged as a particularly interesting candidate based on its phenotypic profile in the screen. This project aimed to characterise its genome-wide binding pattern by ChIP-seq in early *Drosophila* embryos, and to determine whether it shares binding characteristics with known chromatin regulators — particularly the pioneer factor Grainy Head (Grh) and the PcG component Polycomb (Pc).

A specific hypothesis was that CG2129 might function as a **pioneer factor** — a transcription factor capable of binding closed or nucleosomal chromatin and facilitating the establishment of accessible chromatin regions. Pioneer factors are characterised by: (1) binding at transcription start sites (TSS) or enhancers, (2) co-occupancy with active chromatin marks, and (3) ability to establish chromatin accessibility at target loci.

---

## Approach

### Experimental System
ChIP-seq was performed in **2-3h *Drosophila* embryos** — the early post-ZGA window when the first wave of zygotic transcription is established and pioneer factors are most active.

### Bioinformatics Pipeline
```
Raw reads (.fastq)
    ↓ FastQC — quality control
    ↓ Bowtie2 — alignment to dm6 (Drosophila genome)
    ↓ SAMtools — filtering, sorting, indexing
    ↓ MACS2 — peak calling (FDR q < 0.05)
    ↓ ChIPseeker — peak annotation (promoter, gene body, intergenic classification)
    ↓ bedtools intersect — comparison with Grh and Pc binding profiles
    ↓ MEME-ChIP — de novo motif discovery at CG2129 binding sites
    ↓ IGV — genome browser visualisation
```

Tools: FastQC, Bowtie2, SAMtools, MACS2, ChIPseeker, bedtools, MEME-ChIP, IGV (Galaxy web server)

---

## Key Findings

### Finding 1 — CG2129 predominantly occupies promoter regions

ChIPseeker annotation of CG2129 peaks reveals strong enrichment at promoter regions:

| Genomic Feature | Proportion of CG2129 Peaks |
|---|---|
| Promoter (≤1 kb from TSS) | ~91.34% |
| Promoter (1-2 kb) | ~2.64% |
| Promoter (2-3 kb) | ~1.32% |
| Distal intergenic | ~1.98% |
| Other (exon, intron, UTR) | < 2% |

The near-exclusive promoter occupancy — particularly within 1 kb of the TSS — is consistent with a gene-regulatory role and shares characteristics with pioneer factors and TrxG proteins that mark active gene promoters.

### Finding 2 — CG2129 binding is distinct from Grh and Pc

Bedtools intersect analysis comparing CG2129 peaks with Grh and Pc binding profiles at the same developmental stage (2-3h embryo):

- **CG2129 and Grh share only 2.69% of common DNA binding sites** (293 shared sites out of 2,575 CG2129 sites and 8,579 Grh sites)
- CG2129 shows distinct binding patterns compared to both Grh and Pc

This result indicates that CG2129 is not simply redundant with Grh — it occupies a largely independent set of promoter targets. The small overlap (293 sites) could represent a functionally important shared set of target genes worth investigating, but the overall binding profiles are distinct.

### Finding 3 — Genome browser visualisation shows co-occupancy with Grh and Pc at specific loci

Despite the low genome-wide overlap, genome browser views of specific loci show that at certain positions — particularly around the *CG8312/SpdS/D44* region of chr3R:9,483,524-9,724,118 — CG2129, Grh and Pc peaks coincide. The boxed region in this view shows a cluster of co-occupied sites. This suggests that while CG2129 and Grh do not share most binding sites, the sites they do share may represent loci of particular regulatory importance.

### Finding 4 — CG2129 heatmap and profile show sharp TSS enrichment

Heatmap analysis centred on gene TSSs shows:
- Sharp CG2129 signal precisely at the TSS
- Signal falls off rapidly in both directions from the TSS
- Two biological replicates show highly consistent enrichment profiles

This TSS-centred pattern is characteristic of transcription factors and chromatin regulators that function at gene promoters — consistent with a role in marking or activating transcription start sites.

---

## Biological Significance

The near-exclusive TSS occupancy of CG2129, combined with its identification in a TrxG RNAi screen, suggests it may function as a **promoter-binding TrxG regulator** — potentially involved in marking or maintaining active promoter states at its target genes. Its distinct binding profile from Grh suggests it acts on a different set of target genes, potentially regulating a specific transcriptional programme in the early embryo.

The small set of shared targets with Grh (293 sites) is particularly interesting: these loci are bound by both a known pioneer factor and this candidate TrxG regulator simultaneously in the early embryo, potentially representing sites of coordinated regulatory activity. Whether CG2129 functions as a pioneer factor at these shared sites — or requires Grh-established accessibility to bind — is an open question.

---

## Limitations and Honest Assessment

- Gene identity is withheld pending publication; this limits the ability to cross-reference with existing literature on CG2129's function
- Peak overlap analysis (2.69% with Grh) establishes that binding profiles are distinct but does not address whether the shared sites are functionally significant
- No functional validation has been performed — the role of CG2129 at its target promoters has not been tested by depletion or overexpression
- The analysis is limited to the 2-3h embryo; CG2129 binding at other developmental stages has not been examined

---

## Future Directions

1. **Functional characterisation** — deplete CG2129 by RNAi; perform RNA-seq to identify which genes at CG2129-bound promoters show expression changes; this would confirm whether CG2129 binding is functionally required for target gene activation
2. **Chromatin accessibility at CG2129 targets** — perform ATAC-seq in CG2129-depleted embryos to ask whether it has pioneer-like activity in establishing accessibility at its target promoters
3. **Histone mark analysis** — ChIP-seq for H3K4me3 and H3K27ac at CG2129-bound promoters to confirm active chromatin context
4. **Motif analysis** — use MEME-ChIP results to identify the DNA sequence motif recognised by CG2129, which would enable identification of additional target sites and comparison with known TF binding motifs
5. **Analysis of shared CG2129/Grh targets** — the 293 shared binding sites merit specific investigation; are these sites where CG2129 and Grh cooperate? Do they correspond to genes with specific developmental functions?

---

## References

- Khan S. et al. (2021). *Frontiers in Cell and Developmental Biology.* Tariq Lab RNAi screen; Ball as TrxG regulator.
- Blythe S. & Bhatt D. (2020). *Development.* Grh pioneer activity is developmentally regulated.
- Gaskill M. et al. (2021). *eLife.* Zelda and GAF at ZGA.
- Zhang Y. et al. (2012). ChIPseeker — R package for ChIP peak annotation.
