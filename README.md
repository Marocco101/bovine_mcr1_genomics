# Project: From Substitution to Stabilization
**Genomic analysis of co-selection risks in *E. coli***

## 1. Project Overview
This project serves as a technical proof-of-concept for the PhD research proposal by Makiko Fujita-Suzanne.My research focuses on the **"Integron Trap" hypothesis**: the risk that the use of traditional antibiotics considered as safe (Sulfonamides/Trimethoprim) in livestock may co-select for critical resistance genes (such as *mcr-1* for Colistin) due to genetic linkage on mobile genetic elements.

**Objective:**
To demonstrate the aforementioned co-selection mechanism by detecting the co-existence of specific resistance markers in a single *E. coli* genome using WGS.

---

## 2. Phase 1: General Screening (ResFinder)
**Goal:** To establish the baseline resistome of the test isolate and confirm its Multi-Drug Resistant (MDR) status.

**Methodology:**
- **Input:** *E. coli* genome assembly (RefSeq: GCF_001682305.2) retrieved from NCBI.
- **Tool:** ResFinder 4.7.2 (Center for Genomic Epidemiology).
- **Settings:** Acquired resistance genes were identified with a threshold of 90% ID and 60% length.

> **Note on Data Selection (Technical Model):**
> I referred the study (Um et al., 2022), but the raw WGS data from this study was not publicly available. Therefore, I selected **RefSeq strain EC590** to demonstrate a **technical model**. Although this is a human isolate from Malaysia, I chose it because it carries the critical resistance profile of **mcr-1** alongside **sul** and **dfr** genes.

**Results:**
The comprehensive screening using ResFinder confirmed that this isolate carries multiple critical resistance genes.
- **Colistin:** `mcr-1.1` (100% Identity) - *Highest Priority Critical Antimicrobial*
- **Sulfonamides:** `sul1` (100% Identity),`sul2` (100% Identity) - *sul1 is linked to Class 1 Integrons*
- **Trimethoprim:** `dfrA17` (100% Identity) - *Gene cassette often associated with integrons*
- **Beta-lactams:** `blaTEM-1B`

![ResFinder Result](resfinder_result.png)

The interpretation of this analysis is that the simultaneous presence of mcr-1, sul1, sul2, and dfrA17 suggests that resistance to Colistin could be maintained even if only Sulfonamides or Trimethoprim are used.

---

## 3. Phase 2: Targeted Analysis (My Experiment)
**Goal:**
To see if I could specifically detect the particular combination of genes (mcr-1, sul, dfr) using a custom database created by myself.

**My Approach:**
I created a small custom database file [`integron_trap_db.fasta`](integron_trap_db.fasta)  containing only the 4 specific genes I am interested in:
1.  **`mcr-1.1`** (Colistin resistance)
2.  **`sul1`** & **`sul2`** (Sulfonamides resistance)
3.  **`dfrA17`** (Trimethoprim resistance)

- **Tool:** MyDatabase Finder
- **Database:** [`integron_trap_db.fasta`](integron_trap_db.fasta) (Derived from NCBI Reference Sequences)

**Results:**
Four target genes were successfully detected.

| Gene | Identity | My Observation |
| :--- | :--- | :--- |
| **mcr-1.1** | **100.00%** | **Detected.** I confirmed that the colistin resistance gene is present. |
| **sul1 / sul2** | **100.00%** | **Detected.** Both genes were found perfectly. |
| **dfrA17** | **100.00%** | **Detected (Partial).** The identity was 100%, but the length was partial (Grey color). |

![Custom Analysis Result](mydbfinder_custom_result.png)


---
**Proof of Concept for "From Substitution to Stabilization"**
The results from this model analysis provide evidence that supports the core hypothesis of my Ph.D. proposal:

1.  **The Co-selection Mechanism:**
The detection of `sul1` (Class 1 Integron) and `dfrA17` are located so close to `mcr-1`. This implies that the use of **Sulfonamides and Trimethoprim** (Category D "Prudence" antibiotics) creates a selective pressure that maintains **Colistin resistance** (Category B), even when Colistin is not being used. 

2.  **Chromosomal Stabilization:**
In this model strain (EC590), the `mcr-1` gene is interestingly located on the **chromosome** (Accession: `NZ_CP016182.2`, defined as *"Escherichia coli strain EC590 chromosome, complete genome"* by NCBI), not a plasmid. This clearly illustrates the risk of **"Stabilization"**, meaning that resistance genes move from mobile elements to the chromosome and locked-in, making them impossible to eliminate even if antibiotic use is stopped.

3.  **Risk Replacement:**
Reducing Colistin usage in French veal calves may be insufficient if Sulfonamides and Trimethoprim are used as substitutes, as they target the same genetic "Trap."


---
## 4. Phase 3: Visual Verification & Scientific Interpretation
**Goal:**
To go beyond simple detection and visually confirm the physical linkage ("The Trap") of these genes on the genome map.

**Methodology:**
I used the **NCBI Graphics** tool to examine the chromosomal neighborhood of the detected genes.
- **Accession:** `NZ_CP016182.2` (Chromosome)
- **Target Region:** ~3,030,000 bp

**Results & My Observation:**
I successfully visualized the "Integron Trap" structure.

![Integron Trap Map](integron_trap_map.jpg)

* **Observation 1 (The Trap):**
As shown in the map above, **`sul1`** and **`dfrA17`** (as *dihydrofolate reductase*) are located right next to each other. This physical linkage means that using either Sulfonamides and/or Trimethoprim, to replace Colistin, will inevitably co-select for the other.

* **Observation 2 (Stabilization):**
Most importantly, I confirmed that **`mcr-1`**, **`sul1`**, and **`dfrA17`** are all located on the **Chromosome**, not on a plasmid.
This is a critical finding for my Ph.D. proposal. It suggests that these resistance genes have moved from mobile elements to the chromosome, achieving **"Stabilization."** Once stabilized, these genes are vertically inherited and difficult to eliminate, even if antibiotic use is stopped.


---
## 5. Phase 4: Future Work (Ph.D. Plan)
This project validated the detection workflow using a model strain. In my proposed Ph.D. research at ANSES, I will scale this approach:

- **Data Source:** Analyze real-world WGS data from the **RESAPATH** network (French bovine surveillance).
- **Method:** Apply **Spatio-temporal Bayesian Phylodynamics** to quantify the correlation between Sulfonamide/Trimethoprim consumption and the stabilization of these Integron-Plasmid structures (2010–2024).
- **Objective:** To contribute to development of a new risk indicator for ANSES to re-evaluate the environmental risk of substitution antibiotics.

---

## 6. Tools & References
- **NCBI Datasets:** Genome acquisition (RefSeq: GCF_001682305.2).
- **ResFinder 4.1 and  MyDatabase Finder:** Center for Genomic Epidemiology (DTU).
- **Reference Study (Context):** Um et al. (2022), *High Fecal Prevalence of mcr-Positive E. coli in Veal Calves at Slaughter in France*.
- **Proposal:** *From Substitution to Stabilization* (M. Fujita).
