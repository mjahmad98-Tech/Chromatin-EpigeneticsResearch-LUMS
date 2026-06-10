# Ballchen Kinase Domain — Cloning, Expression and Purification

**Project type:** MS Thesis — Wet Laboratory  
**Status:** Completed (2024)  
**System:** *Drosophila melanogaster* / *E. coli* BL21 expression  
**Supervisor:** Dr. Muhammad Tariq, Tariq Epigenetics Lab, LUMS

---

## Biological Motivation

Ballchen (Ball), also known as NHK-1 (Nucleosomal Histone Kinase-1), is a conserved Serine/Threonine kinase and member of the Trithorax group of chromatin regulators in *Drosophila melanogaster*. Its human homolog is VRK1 (Vaccinia-Related Kinase 1), which shares 44% kinase domain identity and is overexpressed in multiple cancer types, making it a candidate therapeutic target.

Ball phosphorylates Histone H2A at Threonine-119 (H2AT119p) — a mark that directly counteracts PRC1-mediated H2AK118 ubiquitination on the adjacent residue of the same histone tail. This competition between H2AT119p (TrxG, active) and H2AK118ub (PcG, repressive) at the same nucleosome is proposed to function as a molecular switch determining whether a gene is maintained in an active or silenced state.

The lab's kinome-wide RNAi screen identified Ball as a TrxG regulator (Khan et al., 2021). Ball depletion causes loss of H2AT119p, a rise in H2AK118ub, and silencing of TrxG target genes — including homeotic and non-homeotic targets. Ball also interacts with CBP to maintain H3K27ac at active loci (Shaukat et al., 2021), placing it at the interface of multiple active chromatin marks.

Despite this established role, the upstream signalling pathways that regulate Ball's kinase activity remain unknown. This is the central gap: Ball connects cell signalling to epigenetic memory, but the signals that activate it — and the downstream chromatin substrates beyond H2A — are not fully characterised.

**The goal of this project was to produce purified Ball kinase domain as a biochemical tool to enable:**
1. In vitro kinase assays to confirm substrate specificity
2. Inhibitor screening to identify compounds that block Ball's catalytic activity
3. Structural studies to understand the kinase-substrate interaction
4. Future identification of upstream signalling pathways through phosphoproteomic approaches

---

## The Kinase Domain

The full-length Ball protein is 599 amino acids (65.994 kDa). The kinase domain spans residues encoded by an 846 bp region, producing a 31.302 kDa domain. This kinase domain is structurally conserved with human VRK1 (44% identity), mouse VRK1 (43%), *Xenopus laevis* VRK (41%), and *C. elegans* VRK (37%), underscoring the evolutionary conservation of this kinase family across metazoans.

The Ball kinase domain contains approximately 40% rare codons relative to standard *E. coli* usage — a critical technical challenge that required a specialised expression strategy.

---

## Methods

### Primer Design and Cloning
- Primers designed with NdeI (N-terminus) and XhoI (C-terminus) restriction sites flanking the 846 bp kinase domain
- 6×His tag incorporated at the C-terminus for affinity purification
- PCR amplification of kinase domain from *Drosophila* cDNA
- Restriction digestion and ligation into pET21a(+) expression vector
- Transformation into *E. coli* DH5α for plasmid propagation
- Colony PCR and double-digestion restriction analysis to confirm successful cloning

**Cloning confirmation:** Double digestion released the expected 846 bp insert alongside the 5,443 bp vector backbone, confirmed by agarose gel electrophoresis.

### Bacterial Expression
- Expression construct transformed into **BL21-CodonPlus (DE3)-RIL** strain — selected specifically because this strain carries additional copies of rare tRNA genes (*argU*, *ileY*, *leuW*), compensating for the high rare codon content in the Ball kinase domain
- Expression induced with IPTG; uninduced control run in parallel
- Both pellet (P) and supernatant (S) fractions collected post-lysis and run on SDS-PAGE
- Target band confirmed at **31.302 kDa** in the induced pellet fraction — absent in uninduced control

### Purification
- Protein expressed in inclusion bodies under denaturing conditions — expected given the high rare codon content and prokaryotic expression of a eukaryotic chromatin-associated kinase
- Cell lysis under denaturing conditions (8M urea)
- **Ni-NTA affinity chromatography** — His-tagged protein captured under denaturing conditions
- Sequential washes (W2, W1) followed by elution fractions (E2, E1)
- Three-day **dialysis** for stepwise refolding: gradual reduction of urea concentration to allow proper protein folding
- Post-dialysis SDS-PAGE confirmed the 31.302 kDa Ball kinase domain in elution fractions

---

## Key Results

| Step | Result |
|---|---|
| Cloning | 846 bp insert confirmed by restriction digestion (NdeI/XhoI) |
| Expression | 31.302 kDa band present in induced pellet; absent in uninduced control |
| Purification | Target band enriched in elution fractions (E1, E2) after Ni-NTA purification |
| Refolding | Protein recovered post-dialysis; band confirmed on post-dialysis SDS-PAGE |

The successful purification of the Ball kinase domain provides the first step toward biochemical characterisation of this TrxG kinase and its role in bridging cell signalling with epigenetic memory.

---

## Limitations and Honest Assessment

- Protein was expressed under denaturing conditions and refolded by dialysis — enzymatic activity of the refolded protein has not yet been confirmed and requires an in vitro kinase assay
- Yield and purity were not quantified by densitometry or Bradford assay in this work
- Whether the refolded kinase domain retains the same conformation as the native protein cannot be confirmed without structural data

---

## Future Directions

1. **In vitro kinase assay** — test whether purified Ball kinase domain phosphorylates H2A-containing nucleosomes or peptide substrates in vitro; confirm T119 specificity
2. **Inhibitor screening** — use the purified domain in a fluorescence-based (FRET or ADP-Glo) kinase assay to screen for small molecule inhibitors; identify compounds that block catalytic activity
3. **Feeding experiments in Drosophila** — validated inhibitors could be administered to Ball-overexpressing flies to test phenotypic rescue; *Drosophila* kinase inhibitor feeding is established in the literature
4. **Phosphoproteomics** — use active Ball kinase to identify downstream substrates beyond H2A by mass spectrometry; this would directly reveal which nuclear factors Ball modifies and which signalling pathways it connects to
5. **VRK1 translational relevance** — given that VRK1 is overexpressed in multiple human cancers and is a synthetic lethal target in VRK2-deficient tumours, inhibitors identified from Ball screening could have direct translational relevance

---

## References

- Khan S. et al. (2021). *Frontiers in Cell and Developmental Biology.* Ball as a TrxG regulator.
- Shaukat A. et al. (2021). *Frontiers in Cell and Developmental Biology.* Ball-CBP interaction and H3K27ac maintenance.
- Aihara H. et al. (2004). *Genes & Development.* NHK-1 protein structure and homology.
- Haider A. et al. (2021). *Frontiers in Cell and Developmental Biology.* Kinome-wide RNAi screen identifying Ball.
- Monte-Serrano E. et al. (2023). *Epigenetics & Chromatin.* VRK1 regulates histone H3 epigenetic modifications.
