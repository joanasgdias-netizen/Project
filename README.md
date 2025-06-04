# Microbiota-Prebiotic Functional Profiling Pipeline

## Overview

This project focuses on understanding how specific prebiotic compounds influence gut microbiota composition and functionality. Using a modular bioinformatics pipeline, we integrate taxonomic profiling with functional prediction to identify microorganisms that respond to prebiotic supplementation and uncover the metabolic enzymes responsible for their growth.

By bridging the gap between microbiota shifts and metabolic capacity, this tool aims to provide mechanistic insights into microbiota-prebiotic interactions, with a special focus on Yacon polysaccharides and microbial cellulose.

---

## Key Features

- 📊 **Statistical analysis** of microbiota composition using MicrobiomeAnalyst  
- 🧬 **Taxonomic profiling** with 16S rRNA sequencing data (pre-analyzed)
- 🔍 **Functional prediction** using KEGG 
- 🧪 **Custom script** to map enzymes to taxa and infer prebiotic degradation capacity  
- 🧠 **Integration** of UPIMAPI for enriched enzyme annotation and pathway mapping  
- 🧱 **Modular design**: start from preprocessed abundance tables

---

## Pipeline Structure

### Phase 1: Normalization
**Goal:** Normalize raw taxonomic abundance data based on 16S rRNA copy number to ensure more biologically meaningful relative abundance
- Input:
  - data_file.csv (output from sequencing pipeline or provider)
  - 16S_copy_numbers.csv (taxon-to-copy-number reference obtained from rrnDB)
- Tools: rrnDB
- Output: matrix_normalized_microbiomeanalyst.csv (a MicrobiomeAnalyst-compatible file)
- Script: normalize_16S_matrix.py

### Phase 2: Statistical Selection of Relevant Taxa
**Goal:** select taxa that: 
  - Significantly change in abundance (p-value)
  - Have meaningul effect size (LDA score)
  - Are consistently present (core microbiome)
  - Show non-negligible relative abundance (Mean abundance)
- Input:
  - univar_test_output.csv
  - taxa_abund.csv
  - lefse_de_output.csv
  - core_microbiome.csv
  (these files are obtained using MicrobiomeAnalyst)
- Tools: MicrobiomeAnalyst
- Output: selected_taxa.csv and excluded_taxa.csv
- Script: select_taxa.py

### Phase 3: Functional Mapping
**Goal:** Link selected bacteria to KEGG pathways by matchng predicted enzymes (EC numbers) to pathways enzyme sets.
- Input:
  - organisms.csv: with Genus and Species columns
  - pathway_ids.txt: list of KEGG pathway IDs (e.g., map00500)
- Tools: KEGG REST API
- Output: compatibility_table_with_names.csv: which bacteria have which enzymes in which pathways
- Script: pathway_bacteria_ec_analysis.py
---

## Requirements
- Python 3.7+
- MicrobiomeAnalyst (web interface)
- Required databases:
  - KEGG REST API
  - rrnDB

---
## Authors and Acknoledgements 
Developed by Vanessa Rodriguez, as part of a Project in a Bioinformatic Master at University of Minho, under the supervision of Professor Clarisse Nobre and Professor Andreia Salvador 

---


