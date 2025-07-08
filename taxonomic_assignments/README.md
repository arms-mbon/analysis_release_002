Here are the output files containing read count tables and taxonomic assignments from the PEMA processing of sequence data from ARMS-MBON's second sampling campaign. These files are the basis for EuroBIS submissions and the manuscript introducing data_release_002.

---

## Extended_final_table Files

The `Extended_final_table` files contain the following information:

### ASV/OTU identifiers of the following format:

- **For COI**: `ASV_XY:ID`
  - The `ID` part matches the ID in the corresponding `tax_assignments` and `.fasta` files.
  - The "ASV" part is unique **within** a single PEMA run, while the "ID" part is unique for each DNA sequence and can occur across runs.
  - Example: `ASV_1` can appear in different runs but doesn't refer to the same DNA sequence across runs. However, the `ID` is consistent.

- **For 18S and ITS**: `OtuXY`
  - Identifiers match the identifiers in the corresponding `.fasta` files.
  - Unique within each PEMA run, but `Otu1` in two runs doesn't represent the same sequence.
  - Due to an error in PEMA when processing ITS, the identifiers are of the format `OtuXY` even though they represent ASVs clustered using Swarm v2.

### Other columns:

- Columns up to the **third last column**: Read counts per sample (material sample IDs).
- **Second last column**: Full taxonomic classification string from the reference database.
  - For COI, PEMA didn’t copy the species-level name; it was added later using code in `code_release_001` (see `updated_taxonomic_assignments` for details).
  - For 18S, taxonomy was curated for compatibility with NCBI and WoRMS (required for EurOBIS submission).

- **Last column**: NCBI taxon ID and taxon name for the lowest assignable level.

---

## Filenames Include:

- Date the samples were sequenced (e.g., `April2021`)
- Marker gene (COI, ITS, 18S)
- `noBlank` tag:
  - a) Negative control samples removed
  - b) Potential contaminants (identified using the R package `decontam`) removed

---

## tax_assignments Files (COI only)

These contain:

- **ASV identifiers** of the format `ID_readAbundance`
  - `ID` matches the ID part in the corresponding `Extended_final_table` file.

- **Taxonomic classification**:
  - For each level: assignment and confidence value, as determined by the RDP classifier.

- **Filenames include**:
  - Date (e.g., `April2021`)
  - Marker gene (`COI`)
  - `noBlank` tag (contaminant ASVs more abundant in blanks than in samples were removed)

Additionally, we provide files indicating:
- Which samples produced no ASVs/OTUs
- Which ASVs/OTUs were removed or adjusted due to blank detection

---

## Taxonomy Correction

The taxonomic assignments from PEMA for **COI** and **18S** have been curated due to various issues. Code is available in:  
 [`code_release_001`](https://github.com/arms-mbon/code_release_001)

### COI (Bug in PEMA v2.1.4)

- Species-level assignments were not copied into `Extended_final_table_XX.xlsx`.
- These were recovered from `tax_assignments` and saved in new:
  - `Extended_final_table_XX_TaxonomyFull.csv` files
  - Same structure, but last two columns updated with species-level name and NCBI ID

### 18S (Curation for WoRMS)

- Original PR2 taxonomy structure is hard to match across databases.
- New:
  - `Extended_final_table_XX_TaxonomyCurated.csv` (last two columns curated)
  - `XXX_TaxonomyCompared.csv`: shows original (col 2) and new classification split into taxon levels (cols 3–12)

Users may choose whether to adopt the curated taxonomy.

### 18S Curation Steps:

1. Split taxonomy string by `;`
2. Replace partial `"var."` strings with `"var."`
3. Replace strings containing `" "`, `"XX"` or `"sp."` with `NA`
4. Remove columns containing only `NA`
5. Rejoin non-NA levels using `_`
6. Split again by `_`
7. Convert `"clade"` → `"Clade"`
8. Create `Species` column by joining genus and lowercase species-like strings
9. Final taxonomy levels:
   - `"Domain", "Supergroup", "Division/Kingdom", "Phylum/Class", "Level_X", "Level_XX", "Level_XXX", "Level_XXXX", "Level_XXXXX", "Species"`
10. Remove `"lineage"` values from species column
11. Manually fix remaining `"var."` strings if above species level
12. Remove numeric characters and hyphens from species-level names

---

## Scripts

- **For 18S**: `FixPEMAtaxassigments_18S_taxonomist.py`
- **For COI**: `FixPEMAtaxassigments_COI_taxonomist.py`
