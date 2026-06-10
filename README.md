# Chromatin-EpigeneticsResearch-LUMS

**Author:** Mujtaba Ahmed  
**Affiliation:** Tariq Epigenetics Lab, Department of Biology, LUMS (Lahore University of Management Sciences), Pakistan  
**Supervisor:** Dr. Muhammad Tariq (PhD, FMI-Basel, Switzerland)  
**Status:** MS completed (2024) | Research Assistant (2024–present)

---

## Overview

This repository documents research conducted in the Tariq Epigenetics Laboratory at LUMS, using *Drosophila melanogaster* as a model system to investigate two interconnected questions:

> **How do cell signalling pathways communicate with the epigenetic machinery to maintain cell-type specific gene expression?**  
> **How does naïve chromatin gain competence to establish and maintain cell fate?**

PcG (Polycomb Group) and TrxG (Trithorax Group) proteins are the principal chromatin regulators that maintain heritable gene expression patterns — silencing genes through H2AK118 ubiquitination and H3K27 trimethylation, or activating them through H2A-T119 phosphorylation, H3K4 trimethylation and H3K27 acetylation. Although these complexes co-exist at target loci regardless of expression state, the signal that tips the balance toward repression or activation remains largely unknown. This work investigates the molecular basis of that gap, from kinase biochemistry to genome-wide chromatin profiling.

---

## Projects

| Project | Description | Approach |
|---|---|---|
| [Ballchen Kinase Domain](./ballchen-kinase/) | Cloning, expression and purification of the Ball kinase domain | Molecular cloning, bacterial expression, Ni-NTA purification |
| [Ballchen ChIP-seq](./ballchen-chipseq/) | Genome-wide localisation of Ballchen at insulator elements in S2 cells | ChIP-seq, ATAC-seq, peak calling, bedtools intersect |
| [Grh Pioneer Factor](./grh-pioneer/) | Temporal analysis of Grh binding and chromatin competence across embryonic development | ChIP-seq, ATAC-seq, multi-timepoint integration |
| [CG2129 — Novel Pioneer Factor](./cg2129-pioneer/) | Genome-wide binding profile of a candidate TrxG regulator from a lab RNAi screen | ChIP-seq, ChIPseeker, MEME-ChIP motif analysis |

---

## Biological Context

The central question driving this work is illustrated by a fundamental paradox in chromatin biology: PcG and TrxG proteins co-occupy the same genomic loci regardless of whether the associated gene is active or silenced. Something decides which complex wins — but the signal that favours PcG repression or TrxG activation remains elusive (Khan et al., 2021; Breiling et al., 2001).

Cell signalling pathways are a plausible candidate for this decision: kinases respond to intra- and extracellular cues, modify nuclear factors, and control a large fraction of cellular processes. Ballchen (Ball), a conserved Serine/Threonine kinase and TrxG regulator, sits at this intersection — its H2A-T119 phosphorylation mark counteracts PRC1-mediated H2AK118 ubiquitination at the same histone tail, providing a direct molecular switch between active and repressive chromatin states.

In parallel, understanding how naïve chromatin first gains competence to receive these decisions requires studying the earliest events of transcriptional activation — including how pioneer transcription factors like Grainy Head (Grh) establish chromatin accessibility in the embryo, and how the subsequent recruitment of PcG/TrxG writers resolves regulatory fate at specific loci.

---

## Model System

All work uses *Drosophila melanogaster* — either S2 Schneider cells (for ChIP-seq) or staged embryos (for developmental analyses). *Drosophila* provides a genetically tractable system with well-characterised PcG/TrxG targets, established tools for chromatin profiling, and conserved chromatin regulatory principles relevant to mammalian biology.

---

## Key Publications from the Tariq Lab

- Khan S. et al. (2021). *Frontiers in Cell and Developmental Biology.* — Ball as a TrxG regulator; H2AT119p counteracts H2AK118ub at TrxG target genes.
- Shaukat A. et al. (2021). *Frontiers in Cell and Developmental Biology.* — Ball interacts with CBP to maintain H3K27ac at active genes.

---

## Contact

**Mujtaba Ahmed**  
22140008@lums.edu.pk  
[LinkedIn](https://www.linkedin.com/in/mujtaba-ahmed)  
Lahore, Pakistan
