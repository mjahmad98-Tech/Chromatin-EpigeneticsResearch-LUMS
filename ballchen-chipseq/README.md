# Ballchen ChIP-seq — Genome-Wide Localisation at Insulator Elements in S2 Cells

**Project type:** Research Assistant — Computational/Genomics  
**Status:** Preliminary observation; analysis ongoing  
**System:** *Drosophila melanogaster* S2 Schneider cells  
**Supervisor:** Dr. Muhammad Tariq, Tariq Epigenetics Lab, LUMS

---

## Biological Motivation

Having established Ballchen (Ball) as a TrxG regulator acting at the level of individual gene promoters (Khan et al., 2021), a natural next question emerges: does Ball also play a role at the level of higher-order chromatin organisation? PcG and TrxG proteins are not only gene-level regulators — they are increasingly understood to participate in the formation and maintenance of topologically associating domains (TADs) and their boundaries. Insulator elements, bound by architectural proteins including CTCF, Cp190 and BEAF-32, define these domain boundaries and prevent inappropriate regulatory cross-talk between neighbouring domains.

If Ball sits at insulator elements alongside these boundary proteins, its H2A-T119 phosphorylation activity at boundary-associated nucleosomes could influence the chromatin environment at domain boundaries — with potential implications for TAD integrity and 3D chromatin organisation. This project investigates whether Ball has a footprint at insulator-associated genomic sites, representing a conceptual extension from linear gene regulation to three-dimensional chromatin architecture.

---

## Key Biological Background

**Insulator proteins in *Drosophila*:**
- **CTCF** — sequence-specific DNA-binding insulator protein; recruits Cp190; required for a small subset (<10%) of domain boundaries in flies (Kaushal et al., 2021)
- **Cp190** — cofactor recruited by CTCF, Su(Hw) and other insulator proteins; required for most promoter-distal boundaries; redistributes to mitotic spindle during cell division (Kaushal et al., 2021, 2022)
- **BEAF-32** — DNA-binding insulator protein enriched at TAD boundaries near housekeeping genes; broad genomic distribution

**Chromatin context at insulator elements:**
Insulator elements in *Drosophila* are typically found at accessible chromatin sites (ATAC-seq positive), often between active (H3K27ac) and repressive (H3K27me3) domains. Cp190-bound non-promoter boundaries separate distinct regulatory domains; their loss leads to regulatory cross-talk between previously insulated loci (Kaushal et al., 2022).

---

## Approach

### Data Sources
- **Ballchen ChIP-seq:** Processed from raw reads in the Tariq Lab (S2 cells)
- **CTCF, BEAF-32, Cp190:** Public datasets — GEO/modENCODE (S2 cells; standard reference datasets)
- **CBP, H3K27ac, H3K27me3:** Public datasets (S2 cells)
- **ATAC-seq:** Public dataset (S2 cells)

*Note: Tracks from different sources were loaded and visualised independently in IGV. Each track is independently auto-scaled. Peaks were called with MACS2 (FDR q < 0.05).*

### Bioinformatics Pipeline
```
Raw reads (.fastq)
    ↓ FastQC — quality control
    ↓ Bowtie2 — alignment to dm6 (Drosophila genome)
    ↓ SAMtools — filtering, sorting, indexing
    ↓ MACS2 — peak calling (q < 0.05)
    ↓ ChIPseeker — peak annotation
    ↓ bedtools intersect — overlap analysis between datasets
    ↓ IGV — genome browser visualisation
```

Tools used: FastQC, Bowtie2, SAMtools, MACS2, ChIPseeker, bedtools, IGV (Galaxy web server and local installation)

---

## Key Observation

Genome browser visualisation across a representative ~1 Mb region of chromosome 3R (chr3R:9,315,446–10,277,826) reveals that **Ballchen signal is enriched at multiple genomic positions co-occupied by CTCF and BEAF-32**, which correspond to sites of sharp chromatin accessibility as shown by ATAC-seq. This pattern of co-localisation at open chromatin boundary sites is visible at multiple positions across the genomic view, not only at one isolated locus.

The region includes the *polyhomeotic* (*phu*) locus — a PRC1 component gene — making the co-localisation of a TrxG kinase with insulator proteins at this boundary region particularly interesting biologically.

The concurrent presence of CBP and H3K27ac at these same sites is consistent with Ball's established TrxG identity and its association with active chromatin marks.

**Important caveat regarding Cp190:** The Cp190 track shows sparse visual signal with tick marks rather than prominent peaks. This is biologically expected: Cp190 is not a primary DNA-binding protein — it is a cofactor recruited indirectly by other insulator proteins, and its ChIP signal is inherently lower than direct DNA-binding factors. Additionally, S2 cells are actively dividing, and Cp190 is known to redistribute to the mitotic spindle during cell division, reducing nuclear ChIP signal in cycling cells. The tick marks shown represent MACS2-called peaks (q < 0.05) at these loci, and the co-localisation claim is based on called peak overlap rather than visual signal height alone.

---

## Results Summary

| Comparison | Observation |
|---|---|
| Ballchen vs CTCF | Co-localisation at multiple open chromatin positions across chr3R |
| Ballchen vs BEAF-32 | Co-localisation at insulator-associated sites across the region |
| Ballchen vs Cp190 | Cp190 peak calls (MACS2) overlap at shared sites; coverage lower (see caveat above) |
| Ballchen vs H3K27ac/CBP | Co-enrichment at active chromatin sites — consistent with TrxG identity |
| Ballchen vs H3K27me3 | Bivalent regions present — both active and repressive marks at some Ballchen-occupied loci |
| Ballchen vs ATAC-seq | Ballchen enrichment corresponds to accessible chromatin regions |

---

## Honest Assessment and Limitations

This is a **preliminary visual observation, not a quantitatively confirmed result.**

- Peak overlap has been visualised in IGV but has not yet been quantified with bedtools intersect to determine what fraction of Ballchen peaks genome-wide overlap with insulator protein sites, or whether that overlap exceeds random expectation
- Datasets originate from different sources and experimental conditions — cross-dataset comparisons must be interpreted with appropriate caution
- Co-localisation in ChIP-seq does not demonstrate physical interaction or functional relevance — that requires orthogonal validation

These limitations are acknowledged openly. The observation is presented as a hypothesis-generating finding that motivates the functional experiments described below.

---

## Biological Significance

If Ballchen co-occupies insulator elements with the core boundary proteins, this raises a precise and testable question: does H2AT119 phosphorylation at boundary-associated nucleosomes influence insulator function or domain boundary integrity? This would extend the PcG/TrxG regulatory logic from individual genes to the architectural framework that organises chromatin domains — a connection supported by emerging evidence that PcG/TrxG proteins contribute to TAD organisation in *Drosophila* (Sexton et al., 2012; Bonev et al., 2017).

---

## Future Directions

1. **Quantitative peak overlap** — bedtools intersect between Ballchen peaks and CTCF/BEAF-32/Cp190 peak files; calculate observed vs expected overlap using shuffled controls
2. **Ball depletion + ATAC-seq** — deplete Ball by RNAi in S2 cells; perform ATAC-seq to ask whether chromatin accessibility at insulator-associated sites is affected
3. **Hi-C in Ball-depleted cells** — assess whether TAD boundary integrity changes upon Ball loss; identify which boundaries are Ball-dependent
4. **Co-immunoprecipitation** — test for physical interaction between Ball and Cp190 or CTCF
5. **H2AT119p ChIP at boundary elements** — map the H2AT119p mark specifically at insulator sites to confirm Ball deposits its mark at these locations

---

## References

- Khan S. et al. (2021). *Frontiers in Cell and Developmental Biology.* Ball as a TrxG regulator.
- Kaushal A. et al. (2021). *Nature Communications.* CTCF loss in Drosophila; Cp190 boundary roles.
- Kaushal A. et al. (2022). Cp190 boundary formation paper.
- Mohana G. et al. (2023). *Cell.* Meta-domains and meta-loops in Drosophila CNS.
- Sexton T. et al. (2012). *Cell.* TAD organisation in *Drosophila*.
