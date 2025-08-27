# TLR4-Targeted Peptide Adjuvant Design with PeptideGPT

This repository provides an end-to-end pipeline for the computational design of peptide adjuvants targeting **Toll-Like Receptor 4 (TLR4)**.  
The pipeline integrates a fine-tuned **PeptideGPT (non-hemolytic)** model with multi-stage filtering, immunoinformatics validation, and MHC-I binding prediction.  

The final outputs are ranked peptide candidates that are:  
- Non-toxic (ToxinPred)  
- Antigenic (VaxiJen)  
- Non-allergenic (AllerTOP)  
- Compatible with MHC-I presentation (MHCflurry)  

---

## Background

Adjuvants are critical components of vaccines, enhancing immune responses and improving long-term protection. This project applies generative artificial intelligence (AI) to design novel peptide-based adjuvants that activate TLR4, a key receptor in innate immunity.  

The methodology combines **data-driven sequence modeling** with **in silico immunoinformatics validation**, ensuring that only biologically plausible, safe, and immunogenic peptides are shortlisted for potential experimental testing.  

---

## Methodology

### 1. Data Acquisition and Filtering
- **Primary source:** IEDB (Immune Epitope Database).  
- Filters applied to ensure biological relevance:
  - Epitope type: linear peptides only.  
  - Assay type: T-cell assays, positive outcomes only.  
  - Host: Homo sapiens (human).  
  - Restriction: MHC Class I.  
  - Length: minimum 8 amino acids.  
- Background negatives: length-matched sequences sampled from UniRef.  

### 2. Model Selection and Fine-Tuning
- Base model: `PeptideGPT_non_hemolytic`.  
- Rationale: avoids generating hemolytic peptides while retaining broad peptide sequence diversity.  
- Fine-tuned on `<TLR4>` conditioned positives vs `<BG>` background negatives.  
- Implemented using Hugging Face Transformers and PyTorch with GPU acceleration.  

### 3. Peptide Generation
- `<TLR4>` prompts used to generate novel peptide sequences.  
- Invalid or non-canonical amino acids removed.  
- Length constraint: 8–30 amino acids.  
- Duplicate sequences removed.  

### 4. Filtering and Evaluation
- Physicochemical filtering: net charge, hydrophobicity, and homopolymer detection.  
- Safety and immunogenicity evaluation with:
  - **ToxinPred**: toxicity prediction.  
  - **VaxiJen**: antigenicity scoring.  
  - **AllerTOP**: allergenicity prediction.  

### 5. MHC-I Compatibility and 9-mer Extraction
- **MHCflurry** applied to evaluate MHC-I binding.  
- Parent peptides automatically trimmed into optimal 9-mer windows.  
- Binding affinity (nM) and presentation scores predicted across multiple HLA alleles.  

### 6. Ranking and Reporting
- Candidates scored on antigenicity, safety, and MHC-I presentation.  
- Composite scoring system used for final ranking.  
- Results exported as CSV/Excel and visualized with figures.  

---

## Results

- A total of **50 peptides were generated** using PeptideGPT.  
- Approximately **90% were predicted non-toxic** (ToxinPred).  
- Filtering reduced the set to **7 top parent candidates**, all non-toxic, antigenic, and non-allergenic.  
- MHCflurry-derived 9-mers showed strong predicted binding to prevalent HLA alleles (e.g., HLA-A*02:01, HLA-B*27:05).  
- Final shortlisted peptides balance safety, antigenicity, and MHC-I compatibility.  

### Key Outputs
- **Parent candidates:** 7 safe and immunogenic peptides.  
- **Trimmed 9-mers:** strong nanomolar binding affinities and presentation scores.  
- **Figures:** heatmaps, bar plots, scatter plots, and safety distribution charts.  

---

## Repository Structure
# TLR4-Targeted Peptide Adjuvant Design with PeptideGPT

This repository provides an end-to-end pipeline for the computational design of peptide adjuvants targeting **Toll-Like Receptor 4 (TLR4)**.  
The pipeline integrates a fine-tuned **PeptideGPT (non-hemolytic)** model with multi-stage filtering, immunoinformatics validation, and MHC-I binding prediction.  

The final outputs are ranked peptide candidates that are:  
- Non-toxic (ToxinPred)  
- Antigenic (VaxiJen)  
- Non-allergenic (AllerTOP)  
- Compatible with MHC-I presentation (MHCflurry)  

---

## Background

Adjuvants are critical components of vaccines, enhancing immune responses and improving long-term protection. This project applies generative artificial intelligence (AI) to design novel peptide-based adjuvants that activate TLR4, a key receptor in innate immunity.  

The methodology combines **data-driven sequence modeling** with **in silico immunoinformatics validation**, ensuring that only biologically plausible, safe, and immunogenic peptides are shortlisted for potential experimental testing.  

---

## Methodology

### 1. Data Acquisition and Filtering
- **Primary source:** IEDB (Immune Epitope Database).  
- Filters applied to ensure biological relevance:
  - Epitope type: linear peptides only.  
  - Assay type: T-cell assays, positive outcomes only.  
  - Host: Homo sapiens (human).  
  - Restriction: MHC Class I.  
  - Length: minimum 8 amino acids.  
- Background negatives: length-matched sequences sampled from UniRef.  

### 2. Model Selection and Fine-Tuning
- Base model: `PeptideGPT_non_hemolytic`.  
- Rationale: avoids generating hemolytic peptides while retaining broad peptide sequence diversity.  
- Fine-tuned on `<TLR4>` conditioned positives vs `<BG>` background negatives.  
- Implemented using Hugging Face Transformers and PyTorch with GPU acceleration.  

### 3. Peptide Generation
- `<TLR4>` prompts used to generate novel peptide sequences.  
- Invalid or non-canonical amino acids removed.  
- Length constraint: 8–30 amino acids.  
- Duplicate sequences removed.  

### 4. Filtering and Evaluation
- Physicochemical filtering: net charge, hydrophobicity, and homopolymer detection.  
- Safety and immunogenicity evaluation with:
  - **ToxinPred**: toxicity prediction.  
  - **VaxiJen**: antigenicity scoring.  
  - **AllerTOP**: allergenicity prediction.  

### 5. MHC-I Compatibility and 9-mer Extraction
- **MHCflurry** applied to evaluate MHC-I binding.  
- Parent peptides automatically trimmed into optimal 9-mer windows.  
- Binding affinity (nM) and presentation scores predicted across multiple HLA alleles.  

### 6. Ranking and Reporting
- Candidates scored on antigenicity, safety, and MHC-I presentation.  
- Composite scoring system used for final ranking.  
- Results exported as CSV/Excel and visualized with figures.  

---

## Results

- A total of **50 peptides were generated** using PeptideGPT.  
- Approximately **90% were predicted non-toxic** (ToxinPred).  
- Filtering reduced the set to **7 top parent candidates**, all non-toxic, antigenic, and non-allergenic.  
- MHCflurry-derived 9-mers showed strong predicted binding to prevalent HLA alleles (e.g., HLA-A*02:01, HLA-B*27:05).  
- Final shortlisted peptides balance safety, antigenicity, and MHC-I compatibility.  

### Key Outputs
- **Parent candidates:** 7 safe and immunogenic peptides.  
- **Trimmed 9-mers:** strong nanomolar binding affinities and presentation scores.  
- **Figures:** heatmaps, bar plots, scatter plots, and safety distribution charts.  

Clone the repository:

```bash
git clone https://github.com/your-username/tlr4-peptidegpt.git
cd tlr4-peptidegpt
pip install -r requirements.txt
```
## Dependencies

This project requires the following packages:

- `transformers`
- `torch`
- `peft`
- `pandas`, `numpy`, `biopython`
- `matplotlib`, `seaborn`
- `scikit-learn`, `tqdm`
- `mhcflurry`

---

## Usage

### 1. Prepare Input Data

Place the following input files in the `data/` directory:

- `peptideTLR4data.csv` (IEDB export)
- `uniref102K.fasta` (UniRef sequences)

### 2. Run the Pipeline

Open and execute the notebook:

```bash
notebooks/Finalnotebook.ipynb
```
### 3. Pipeline Steps

- Fine-tune `PeptideGPT_non_hemolytic`
- Generate peptides using `<TLR4>` prompts
- Filter and evaluate generated sequences using:
  - **ToxinPred**
  - **VaxiJen**
  - **AllerTOP**
- Run **MHCflurry** for 9-mer binding predictions

---

### 4. Review Outputs

- Candidate peptides: `runs/samples/`
- Visualizations: `figures/`

---

## Outputs

- Ranked lists of parent peptides and 9-mer subpeptides
- Training and validation metrics
- Generation and filtering reports

### Visualizations Include:

- Heatmaps of properties  
- Antigenicity bar plots  
- Charge vs. hydrophobicity scatter plots  
- MHC-I binding and presentation plots

---

## Disclaimer

This repository provides **computational predictions only**.  
All peptides must be **experimentally validated** before any translational or clinical application.

---

## Citation

If you use this repository, please cite:

**Author:** Sara Al Fliti, Amjad Alqahtani, Shahla Alshaar, Yomna Ali, Fatimah Alhassan   
**Title:** *AI-Driven Design of Universal Peptide Adjuvants for Cost-Effective Vaccines* (2025)



