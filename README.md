# 🚀 TLR4-Targeted Peptide Adjuvant Design with PeptideGPT  

This repository contains an **end-to-end pipeline** for the **computational design of peptide adjuvants** targeting **TLR4 (Toll-Like Receptor 4)**.  
The workflow uses **PeptideGPT (non-hemolytic)** for peptide generation, combined with multi-stage filtering, **MHC-I binding predictions**, and external immunoinformatics tools.  

The pipeline produces **validated, ranked peptide candidates** that are:  
- ✅ Non-toxic (ToxinPred)  
- ✅ Antigenic (VaxiJen)  
- ✅ Non-allergenic (AllerTOP)  
- ✅ Compatible with MHC-I presentation (MHCflurry)  

---

## 📌 Features  

- Fine-tune **PeptideGPT_non_hemolytic** on curated IEDB immune epitope data (positives) vs UniRef negatives.  
- Generate novel peptide candidates conditioned on `<TLR4>`.  
- Apply **filtering**: charge, hydrophobicity, homopolymer runs, peptide length.  
- Evaluate candidates using:  
  - ToxinPred → Toxicity check  
  - VaxiJen → Antigenicity score  
  - AllerTOP → Allergenicity prediction  
  - MHCflurry → MHC-I binding & presentation (automatic 9-mer trimming)  
- Rank peptides with a composite scoring system.  
- Visualize results with **heatmaps, bar plots, scatter plots, and safety distributions**.  

---

## 📊 Results Summary  

- **50 peptides generated** by PeptideGPT  
- ~**90% predicted non-toxic** (ToxinPred)  
- Filtering + ranking → **7 top parent candidates**  
- MHCflurry trimmed peptides to **9-mers** → ensured **MHC-I compatibility**  
- Final shortlist includes strong **antigenic, safe 9-mers** with nanomolar binding affinities to common HLA alleles (e.g., HLA-A*02:01, HLA-B*27:05)  


## 📂 Repository Structure  

