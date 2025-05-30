# Local-Global-Alignment-Tools
Local and global alignment tools, as well as an edit-graph plot.

## Overview

This repository provides a small R library for performing **local** and **global** sequence alignments (Smith–Waterman and Needleman–Wunsch variants) and visualizing the resulting edit graph:

- **Local alignment** via `find_lsa()`  
- **Global alignment** via `find_gsa()`  
- **Edit-graph plotting** via `plot_edit_graph()`  
- **Pretty-printing** of local alignments via `print_local_alignment()`  
- **Pretty-printing** of global alignments via `print_gsa()`  

Two example DNA sequence pairs are included:

1. Short test sequences (`s1` vs. `s2`)  
2. Longer ACE2 haplotype sequences (`s5` vs. `s6`)  

## Prerequisites

- **R** (version ≥ 4.0)  
- The **tidyverse** package  

## Installation

1. **Install R** from [CRAN](https://cran.r-project.org/).  
2. Open R (or RStudio) and install **tidyverse**:
   ```r
   install.packages("tidyverse")
3. Clone or download this repository to your local machine.

## Directory Structure

Local-Global-Alignment-Tools/

├── `local-global.R`    # alignment functions & examples

├── `README.md`          # this file

└── `myalignment.txt`    # alignment result file from script


## Quick Start
1. Open `local-global.R` in your R environment.
2. Source the file

       source("seq_alignment.R")
3. Run local alignment on the example short sequences:

       result_lsa <- find_lsa(s1, s2, sigma = 3, mu = 2)
       print_local_alignment(result_lsa)
       plot_edit_graph(result_lsa$s, result_lsa$b)
4. Run global alignment on the same sequences:
   
       result_gsa <- find_gsa(s1, s2, sigma = 3, mu = 2)
       # write to file:
       print_gsa(
           b      = result_gsa$b,
           v      = result_gsa$vectorV,
           w      = result_gsa$vectorW,
           i      = nrow(result_gsa$b),
           j      = ncol(result_gsa$b),
           fn     = "user_alignment.tsv"
       )

## Custom Usage
- Replace s1, s2 with any two character strings to align arbitrary sequences.
- For the ACE2 haplotypes, use s5, s6 as defined in the script.
- Adjust the gap penalty (sigma) and mismatch penalty (mu) to suit your scoring scheme.

## Outputs
- **Console:** sequence lengths and alignment text.
- **Plot:** edit-graph window in R’s graphics device.
- **File:** `user_alignment.tsv` for results from "Quick Start" section; `myalignment.txt` for original unedited code execution.

## Troubleshooting
- **Performance:** very long sequences (>5 000 residues) may run slowly in pure R loops.
