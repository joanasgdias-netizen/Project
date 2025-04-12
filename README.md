# Microbiota-Prebiotic Functional Profiling Pipeline

## Overview

This project focuses on understanding how specific prebiotic compounds influence gut microbiota composition and functionality. Using a modular bioinformatics pipeline, we integrate taxonomic profiling with functional prediction to identify microorganisms that respond to prebiotic supplementation and uncover the metabolic enzymes responsible for their growth.

By bridging the gap between microbiota shifts and metabolic capacity, this tool aims to provide mechanistic insights into microbiota-prebiotic interactions, with a special focus on Yacon polysaccharides and microbial cellulose.

---

## Key Features

- 📊 **Statistical analysis** of microbiota composition using MicrobiomeAnalyst  
- 🧬 **Taxonomic profiling** with 16S rRNA sequencing data (raw or pre-analyzed)
- 🔍 **Functional prediction** using GUMPP which integrates: PICRUSt2, KEGG, CAZy, and MetaCyc  
- 🧪 **Custom script** to map enzymes to taxa and infer prebiotic degradation capacity  
- 🧠 **Integration** of UPIMAPI for enriched enzyme annotation and pathway mapping  
- 🧱 **Modular design**: start from raw FASTQ files or preprocessed abundance tables

---

## Pipeline Structure

### Phase 1: Taxonomic Profiling
- Input: Raw FASTQ files or pre-analyzed taxonomic tables
- Tools: GUMPP, MicrobiomeAnalyst
- Output: List of microbial taxa enriched in response to prebiotics

### Phase 2: Functional Analysis
- Input: Taxa identified in Phase 1
- Tools: GUMPP (PICRUSt2), KEGG, CAZy, UPIMAPI
- Output: Enzyme profiles and metabolic pathway predictions linked to prebiotic metabolism

---

## Requirements

- Python 3.7+
- QIIME2
- GUMPP
- MicrobiomeAnalyst (web interface)
- UPIMAPI (for UniProt annotation)
- Required databases:
  - KEGG
  - MetaCyc
  - CAZy

---


