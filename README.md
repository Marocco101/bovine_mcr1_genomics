# Project: From Substitution to Stabilization
**Genomic analysis of co-selection risks in *E. coli***

## 1. Project Overview
This project serves as a technical proof-of-concept for the PhD research proposal by Makiko Fujita-Suzanne.
My research focuses on the **"Integron Trap" hypothesis**: the risk that the use of traditional antibiotics considered as safe (Sulfonamides/Trimethoprim) in livestock may co-select for critical resistance genes (such as *mcr-1* for Colistin) due to genetic linkage on mobile genetic elements.

**Objective:**
To demonstrate the aforementioned co-selection mechanism by detecting the co-existence of specific resistance markers in a single *E. coli* genome using WGS.

---

## 2. Phase 1: General Screening (ResFinder)
**Goal:** To establish the baseline resistome of the test isolate and confirm its Multi-Drug Resistant (MDR) status.

**Methodology:**
- **Input:** *E. coli* genome assembly (RefSeq: GCF_001682305.2) retrieved from NCBI.
- **Tool:** ResFinder-4.7.2 (Center for Genomic Epidemiology).
- **Settings:** Acquired resistance genes (Threshold: 90% ID, 60% Length).

**Results:**
The screening confirmed that this isolate carries multiple critical resistance genes supporting the MDR profile.
- **Colistin:** `mcr-1.1` (100% Identity) - *Highest Priority Critical Antimicrobial*
- **Sulfonamides:** `sul1` (100% Identity),`sul2` (100% Identity) - *sul1 is linked to Class 1 Integrons*
- **Trimethoprim:** `dfrA17` (100% Identity) - *Gene cassette often associated with integrons*
- **Beta-lactams:** `blaTEM-1B`

![ResFinder Result](resfinder_result.jpg)

*(Interpretation: The simultaneous presence of mcr-1, sul1, sul2, and dfrA17 suggests that resistance to Colistin could be maintained even if only Sulfonamides or Trimethoprim are used.)*

---

## 3. Phase 2: Targeted Analysis (MyDBFinder)
**Goal:** To verify the "Integron Trap" hypothesis by specifically detecting the linkage of these co-selection markers using a custom-built database.

**Methodology (Planned):**
I will construct a custom FASTA database containing only the specific targets (`mcr-1`, `sul2`, `sul2`, `dfrA17`) and perform a targeted search using **MyDatabase Finder**.

- **Custom Database:** `integron_trap_db.fasta` *(To be uploaded)*
- **Tool:** MyDatabase Finder (CGE).

**Results:**
*(Analysis in progress... Results will be updated here)*

---

## 4. Tools & References
- **NCBI Datasets:** For genome acquisition.
- **ResFinder & MyDatabase Finder:** Genomic analysis tools provided by DTU.
- **Reference:** Research Proposal *"From Substitution to Stabilization"* (M. Fujita).
