# Project 2: Validation on French Veal Surveillance Data

**Target Data:** ANSES Historical Isolate (2016)

**Analysis Type:** Genomic confirmation of the "Integron Trap" in field data.

## 1. Objective
To validate if the co-selection mechanism (genetic linkage between Sulfonamide and Trimethoprim resistance) identified in the model strain (Project 1) is also present in actual field isolates from French livestock.

## 2. Dataset Information
I selected a genomic dataset previously reported by the ANSES Lyon team to benchmark my hypothesis against real-world scenarios.

* **Study:** Valat, Haenni, Madec et al. (2016)
* **Source:** Veal Calves in France (High-risk ESBL clone)
* **Accession:** `LMBK01000000` (WGS Assembly)
* **Isolate ID:** E. coli strain 22593

## 3. Methodology
I applied a two-step validation process:
1.  **Comprehensive Profiling (ResFinder):** To identify variants or alternative resistance genes that the custom database might miss.
2.  **Targeted Search (MyDatabase Finder):** Using my custom database (`mcr-1`, `sul1`, `dfrA17`) that I create for the Project 1 to screen for specific markers.
3.  **Visual Verification (NCBI Graphical Sequence Panel):** To confirm physical linkage on the chromosome/plasmid.

## 4. Results: Multi-Layered Trap Structures

The analysis revealed a complex resistance landscape. Unlike the model strain, this field isolate possesses **three distinct co-selection pairs**, indicating a highly stabilized multidrug-resistant genotype.

### 4.1. Detection of Critical Markers
My custom database successfully detected **`mcr-1` (Colistin resistance)** and **`sul1` (Sulfonamide resistance)** in this French isolate.

![Targeted Analysis Result](mydbfinder_custom_result_frenchveal.png)

### 4.2. Gene Substitution (dfrA17 → dfrA1/dfrA36)
While the model strain (EC590) carried `dfrA17`, the ResFinder analysis revealed that this French isolate utilizes different variants: **`dfrA1`** and **`dfrA36`**. This highlights the evolutionary flexibility of the trap mechanism.

### 4.3. Identification of Three "Trap" Pairs
I identified three independent genomic locations where Sulfonamide and Trimethoprim resistance genes are physically linked. This redundancy makes the resistance extremely difficult to lose.

* **Pair A (Strongest Evidence):**
    * **Location:** `NZ_LMBK01000588.1`
    * **Genes:** **`sul1`** + **`dfrA1`**
    * **Context:** A typical Class 1 Integron structure.
* **Pair B (Confirmation):**
    * **Location:** `NZ_LMBK01000312.1`
    * **Genes:** **`sul1`** + **`dfrA1`**
    * **Context:** Reaffirms the prevalence of this combination.
* **Pair C (Variation):**
    * **Location:** `NZ_LMBK01000112.1`
    * **Genes:** **`sul2`** + **`dfrA36`**
    * **Context:** Shows that `sul2` is also involved in co-selection traps with different partners.

### 4.4. Visual Verification (Pair A)
Using NCBI Graphical Sequence Panel, I confirmed the physical linkage of Pair A on the contig.

* **Contig:** NZ_LMBK01000588.1
* **Coordinates:** `dfrA1` (4660..5133) and `sul1` (6522..7361)
* **Distance:** Approx. 1.4kb (Adjacent)

<img src="integron_trap_map_frenchveal.jpg" alt="French Veal Map (sul1 + dfrA1)" width="800">

## 5. Conclusion & Connection to Ph.D.

### 5.1. Genomic Validation
This analysis proves that the **"Integron Trap" is a reality** in French livestock. The physical linkage of *sul1* and *dfrA1* on a plasmid in the 2016 isolate demonstrates that the mechanism for co-selection was already established and mobile a decade ago.

### 5.2. The "EcoAntibio 2" Paradox (RESAPATH Data)
Recent surveillance data from RESAPATH reveals a critical anomaly. While the French national plan "**EcoAntibio 2**" successfully reduced Colistin resistance initially, a concerning **rebound has been observed since 2019**.
As shown in the chart below, this rise in **Colistin resistance (Purple line)** appears to coincide with the sharp increase in **Trimethoprim-Sulfonamide resistance (Brown line)** and **Sulfonamide resistance (Dark Green)**.

![RESAPATH Trend 2006-2024](resapath_trend_2024.png)

### 5.3. Hypothesis: From Plasmid to Chromosome?
I hypothesize that this 2019 rebound marks a shift in the genetic architecture of resistance.
* **Mechanism:** The continued use of "safe" antibiotics (Sulfonamides/Trimethoprim) has likely maintained *mcr-1* via the trap mechanism.
* **Stabilization:** The synchronized rising trend suggests that the trap structure (seen on a plasmid in 2016) may have been **integrated into the chromosome** in recent years. This would explain why Colistin resistance is increasing despite the reduction in Colistin usage—it has become "locked in" by the selection pressure of other drugs.

### 5.4. Research Proposal
My Ph.D. project aims to verify this **"Plasmid-to-Chromosome Transition"** using large-scale genomic epidemiology. By comparing historical isolates (like LMBK) with post-2019 isolates, I will quantify how much of this "stabilized resistance" is driving the current failure of reduction policies.
