# Grh Pioneer Factor — Temporal Analysis of Chromatin Competence During Drosophila Embryogenesis

**Project type:** Research Assistant — Computational/Genomics  
**Status:** Completed analysis; findings preliminary  
**System:** *Drosophila melanogaster* staged embryos  
**Supervisor:** Dr. Muhammad Tariq, Tariq Epigenetics Lab, LUMS

---

## Biological Motivation

A central question in developmental biology is how naïve chromatin — packaged in an unspecified state at fertilisation — progressively gains the competence to establish and maintain cell-type specific gene expression patterns. Pioneer transcription factors are a key part of this process: unlike conventional transcription factors, they bind closed or nucleosomal chromatin and facilitate the establishment of accessible chromatin regions that subsequently recruit additional regulatory proteins.

Grainy Head (Grh) is a highly conserved pioneer transcription factor essential for epithelial cell fate determination in *Drosophila* and across metazoans. Its pioneering activity is developmentally regulated — it functions as a pioneer in the larval eye imaginal disc but is not required for establishing chromatin accessibility in the early embryo (Blythe & Bhatt, 2020, *Development*). This context-specificity makes Grh an informative model for studying how pioneer factor function is modulated across developmental time.

Zygotic genome activation (ZGA) in *Drosophila* occurs around 2-3 hours post-fertilisation — the point at which the embryonic genome is first transcribed. At ZGA, chromatin is at its most plastic: broadly accessible, with histone modification patterns not yet resolved into stable active or repressive states. Understanding how chromatin transitions from this plastic early state to a state of defined, heritable gene expression is fundamental to understanding cell fate establishment.

**The central question this project addresses:**  
*Does pioneer factor binding alone explain chromatin accessibility and regulatory fate, or does the subsequent recruitment of PcG/TrxG writers determine the outcome?*

---

## Key Biological Background

**Pioneer factors at ZGA:**  
ZGA in *Drosophila* is primarily driven by the maternally provided zinc-finger factor Zelda — the major pioneer factor of the early embryo. GAF (GAGA factor, encoded by *Trl*) also contributes to ZGA chromatin accessibility. Grh is expressed at ZGA and increases in abundance throughout embryogenesis, but unlike Zelda, Grh is not required for establishing early embryo chromatin accessibility (Blythe & Bhatt 2020; Gaskill et al. 2021).

**PcG/TrxG writers:**  
- **CBP** — writes H3K27ac (active mark); TrxG co-activator; interacts directly with Ball
- **PRC2 / E(z)** — writes H3K27me3 (repressive mark); catalytic subunit of PRC2
- **Pc, Pho** — PRC1 components; Pho is a DNA-binding PcG protein
- **Trl (GAF)** — TrxG member; chromatin remodeller; pioneer factor at ZGA
- H3K27ac and H3K27me3 are mutually exclusive at the same H3 tail — the balance between them is determined by which writer is recruited

---

## Approach

### Data Sources
All datasets are publicly available ChIP-seq and ATAC-seq data from staged *Drosophila melanogaster* embryos, processed and visualised for this analysis.

| Track | Timepoint | Source |
|---|---|---|
| Grh ChIP-seq | 3h, 12h, 16-20h | Published datasets |
| CBP ChIP-seq | 3h, 16-20h | Published datasets |
| Pc ChIP-seq | 14-16h, 16-20h | Published datasets |
| Pho ChIP-seq | 16-20h | Published datasets |
| Trl ChIP-seq | 16-20h | Published datasets |
| H3K27ac ChIP-seq | 3h, 16-20h | Published datasets |
| H3K27me3 ChIP-seq | 3h, 16-20h | Published datasets |
| ATAC-seq | 2-3h, 16-20h | Published datasets |

### Bioinformatics Pipeline
```
Raw reads (.fastq)
    ↓ FastQC — quality control
    ↓ Bowtie2 — alignment to dm6
    ↓ SAMtools — filtering, sorting, indexing
    ↓ MACS2 — peak calling (FDR q < 0.05)
    ↓ deepTools — bigwig generation, signal normalisation
    ↓ IGV — multi-track genome browser visualisation
    ↓ Integration across timepoints
```

---

## Key Findings

### Finding 1 — Grh binding increases progressively over development but does not predict mark identity at early stages

At 2-3h (ZGA), Grh occupies chromatin broadly. However, histone mark distribution at Grh-bound loci is locus-specific and not correlated with Grh occupancy — some loci carry H3K27ac, others H3K27me3, and some show both marks simultaneously (bivalency). **This is consistent with published evidence** that Grh is not required for establishing chromatin accessibility in the early embryo (Blythe & Bhatt, 2020) and that ZGA accessibility is driven by Zelda and GAF rather than Grh.

At 12h and 16-20h, Grh binding expands and intensifies genome-wide. The progressive increase in Grh occupancy — from sparse at 3h to dense at 16-20h — is consistent with Grh's developmentally modulated pioneer activity increasing as the embryo matures.

### Finding 2 — At 16-20h, histone mark identity becomes locus-specific and correlates with writer co-recruitment

At 16-20h, the full complement of PcG/TrxG writers is recruited: Pc, Pho, Trl (GAF), and CBP are all present alongside Grh. Critically, the distribution of H3K27ac and H3K27me3 becomes locus-specific at this stage — correlating with which writer is present at each locus. Where CBP is enriched, H3K27ac is present and ATAC-seq shows accessible chromatin; where PRC2 dominates, H3K27me3 is present and chromatin is less accessible.

**Grh binding alone does not predict which mark is deposited** — the same broadly distributed Grh occupancy is seen at loci that will become active (H3K27ac) and at loci that will become repressed (H3K27me3). The regulatory fate is determined by the writer that is subsequently recruited, not by Grh occupancy per se.

### Finding 3 — Chromatin accessibility correlates with writer co-recruitment, not pioneer binding alone

Integrating ATAC-seq with the ChIP-seq datasets shows that at 16-20h, chromatin accessibility is highest at loci where CBP and H3K27ac are enriched — coinciding with Grh occupancy but not explained by it. This supports the interpretation that **Grh bookmarks loci early**, establishing a permissive context, but the **modification landscape deposited by subsequently recruited writers determines the regulatory outcome**.

---

## Interpretation in Context of Current Literature

This observation fits within the broader framework of context-specific pioneer factor activity:

- **Blythe & Bhatt (2020)** showed Grh is not required for early embryo chromatin accessibility — consistent with our observation that at 3h, Grh binding does not correlate with or predict chromatin accessibility
- **Gaskill et al. (2021)** demonstrated that Zelda and GAF are the primary drivers of ZGA accessibility — the broad accessibility seen at 3h in ATAC-seq reflects Zelda/GAF activity, not Grh
- The progressive increase in Grh's correlation with accessibility from 3h to 16-20h is consistent with Grh's pioneer activity being **developmentally modulated** — becoming more instructive at later stages when it is expressed in specific tissues and contexts

The finding that writer recruitment — rather than pioneer binding — determines regulatory fate also connects to the PcG/TrxG paradox: both complexes can co-occupy the same locus (as seen in bivalent domains at 3h), and the balance between them depends on which writer is activated. The signal that tips that balance remains elusive — and is directly connected to the cell signalling gap that Ball kinase occupies.

---

## Limitations and Honest Assessment

- Analysis is based on publicly available datasets from different experimental sources; cross-dataset comparisons must be interpreted carefully
- The chromatin coordinates examined (chr3R:6,717,652–22,115,730) represent a broad genomic window chosen for its diversity of gene types; locus-specific validation at known Grh targets has not been performed
- Correlation between writer recruitment and accessibility does not prove causality; functional validation requires Grh depletion experiments (proposed below)
- This is an observational study — statistical quantification of correlations between ChIP-seq tracks has not yet been performed

---

## Future Directions

1. **Grh depletion experiments** — deplete maternal and/or zygotic Grh using heat-shock inducible RNAi (to avoid early lethality) or FLP-FRT at specific timepoints; perform ATAC-seq to ask whether accessibility at Grh-bound loci is specifically affected at later stages
2. **CBP depletion via tissue-specific UAS-GAL4** — deplete CBP in a spatially restricted manner to ask whether H3K27ac loss at Grh-bound loci specifically impairs accessibility; use CUT&TAG at Grh sites for precise locus-level readout
3. **Zoom into known Grh target loci** — perform locus-specific analysis at validated Grh targets to ask whether the writer recruitment pattern observed genome-wide holds at specific biologically relevant loci
4. **Integration with RNA-seq** — correlate the chromatin accessibility and histone mark changes with gene expression data to confirm that the modification landscape changes are functionally associated with transcriptional outcomes
5. **Connect to 3D genome organisation** — given evidence that loop anchor chromatin gains accessibility during neuronal differentiation (Mohana et al., 2023), ask whether Grh-established accessible loci in the embryo correspond to future meta-loop anchors in differentiated neurons

---

## Broader Significance

This work sits at the intersection of two important fields: pioneer factor biology and 3D genome organisation. The finding that pioneer binding alone is insufficient — that the chromatin modification landscape established by subsequently recruited writers is what determines regulatory fate — has implications beyond individual gene regulation. Recent work has shown that pioneer factors including Lola-I are required for mega-scale chromosomal loop formation in neurons (Gambetta lab, *Genes & Development* 2025). The logic observed here — pioneer factor establishes a chromatin context; what is recruited next determines the outcome — may operate at the scale of individual genes and at the scale of megabase-range regulatory contacts alike.

---

## References

- Blythe S. & Bhatt D. (2020). *Development.* Grh pioneer activity is developmentally regulated.
- Gaskill M. et al. (2021). *eLife.* GAF and Zelda at ZGA.
- Khan S. et al. (2021). *Frontiers in Cell and Developmental Biology.* Ball as TrxG regulator.
- Shaukat A. et al. (2021). *Frontiers in Cell and Developmental Biology.* Ball-CBP interaction.
- Mohana G. et al. (2023). *Cell.* Meta-domains and meta-loops in Drosophila CNS.
- Gambetta lab (2025). *Genes & Development.* Lola-I and meta-loop formation.
