# analysis_release_002
Here are the output files containing read count tables and taxonomic assignments from the PEMA processing of sequence data from ARMS-MBON's second sampling campaign. These files are the basis for EuroBIS submissions and the manuscript introducing data_release_002.

The Extended_final_table files contain the following information:

ASV/OTU identifiers of the following format:

For COI: ASV_XY:ID. The ID part matches the ID in the corresponding tax_assignments and fasta files. The "ASV" part of the identifier is unique within a single PEMA run, while the "ID" part is unique for each DNA sequence and can therefore occur in files across processing runs. This means that while the "ASV_1" prefix for example can occur in each sequencing run, it does not necessarily represent the same DNA sequence in these runs, while the ID is unqiue across all runs for each unique sequence.
For 18S and ITS: OtuXY. The identifiers match the identifiers in the corresponding fasta files for each run and they are unique within a single PEMA run. This means that while "Otu 1" for example can occur in each sequencing run, it does not necessarily represent the same DNA sequence across runs. Unique sequences across runs can be identified by matching OTUs/ASVs to the seqeuences in the fasta files. Because there was an error within PEMA at the time of usage regarding the sequence identifier format for ITS runs, the sequence identifiers in these files are of the format OtuXY. However, these sequences represent ASVs clustered with Swarm v2.
The read counts for each ASV/OTU in each sample that was processed, i.e., columns up to the third last column represent material sample IDs.

The second last column contains the full taxonomic classification as returned by the respective reference database in a single character string. NOTE: For the COI data, the version of PEMA used did not copy the species-level name to the Extended_final_tables: we did this subsequently, using code you can find in code_release_001, and see updated_taxonomic_assignments for more detail on what was done. NOTE: For the 18S data, we curated the taxonomy so they could be better assigned NCBI IDs and matched to WoRMS IDs (a necessary for submitting the data to EurOBIS). 

The last column contains the NBCI taxon ID and taxon name for the lowest taxonomic level the respective ASV/OTU could be assigned to and for which and NCBI taxon ID could be found.

The filenames contain:

The date the samples were sequenced (e.g., April2021)
The marker gene (i.e., COI, ITS, 18S)
The noBlank denotion: This means that a) negative control samples were already removed; b) potential contaminant sequences (identified using the R package *decontam*) were removed

The tax_assignements files are only generated for COI data and contain:

ASV identifiers of the format ID_readAbundance. The ID part matches the ID part in the corresponding Extended_final_table file (see above).

For each level in the taxonomic classification: its assignment and corresponding confidence value as determined by the RDP classifier used for COI classification.

These documents include detailed classifications beyond the genus level for each ASV provided in the Extended Final Tables.

The filenames contain:

The date the samples were sequenced (e.g., April2021)
The marker gene (only COI in this case)
The noBlank dentotion, which means potential contaminant ASVs that were more abundant in the negative control samples compared to actual samples were removed.
We also provide files indicating which samples produced no ASVs/OTUs and which ASVs/OTUs were removed or whose counts were adjusted because they occurred in the blanks.

# Taxonomy correction

The taxonomic assignments from PEMA for COI and 18S from the batch 2 processing of the ARMS-MBON data have been curated by us to accommodate some issues. The code is available in code_release_001[https://github.com/arms-mbon/code_release_001].

Due to a bug in V2.1.4 of PEMA (fixed in new version but not in use at the time of analyses), the assignments in the Extended_final_table_XX.xlsx files for COI in the taxonomic_assignments folder are only denoted to the genus level. The species-level assignments can be found in the tax_assignments files that accompany those final tables. We have extracted those species-level assignments and inserted those, together with newly-minted species-level NBCI IDs, into new Extended_final_table_XX_TaxonomyFull.csv files (note: CSV rather than XLSX), which are the same as the original files but with the final two columns replace with the values.

For the Extended_final_table_XX.xlsx files for 18S, the taxonomy returned from the PR2 database is not so straightforward to compare to taxonomies from other databases due to its unique organisation of taxon nodes used. In order to make more sensible use of these taxonomy results for our subsequent need to match the taxonomic assigments to WoRMS (World Register of Marine Species), we have undertaken a curation of the taxonomic classification for 18S. We have created new Extended_final_table_XX_TaxonomyCurated.csv files (note: CSV rather than XLSX) that are exactly the same as the original files, but contain the new results in the final two columns instead of the previous; and a comparison of the previous and new full taxonomic classifications can be found in the files called XXX_TaxonomyCompared.csv (e.g. April2021_18S_noBlank_TaxonomyCurated.csv) with the OTUID (col 1), the original classification (col 2), and the new classification broken into taxon levels (cols 3-12). It is up to the user to decide whether they wish to adopt these curations for their own work, or not. For the specific case of 18S taxonomy, strings assigned by the PR2 database were curated as follows:

Separate taxonomy strings into separate columns by ";"

Strings partially containing "var." will be entirely repalced by "var."

Strings containing a space, "XX" or "sp." are set as NA (this step is missing a couple of cases where species assignments are actually present but are in such a cryptic format that no general code that worked on all other cases could also retrieve those ones. This happens for cases where genus and species are for example in the following format: Phascolopsis;Phascolopsis (strain);gouldii (Phascolopsis (strain)). The species part at the end is not recognized with the code above and we could not come up with a rule that fits takes care of all other cases as well as this one. We just had to accept this as trade-off. The taxonomy strings from the PR2 database are just too cryptic in some cases.).
Remove columns that now only contain NAs

Paste all columns back together into one string ignoring NAs and using "_" as delimiter. This step gets rid of NAs within a taxonomy.

Separate taxonomy strings back into separate columns by "_"

Change lowercase "clade" strings to uppercase "Clade" strings

Create a Species column combining species and genus level strings in one string. This is done by checking for strings which do not have a capital letter (i.e., species level names) and pasting them together with the string in the preceding column.

Final taxonomy levels are then set as follows: "Domain","Supergroup","Division/Kingdom","Phylum/Class","Level_X","Level_XX","Level_XXX","Level_XXXX","Level_XXXXX","Species"

Species level strings containing the "lienage" string are set as NA

Some taxonomic levels above the species level may have a "var." string remaining. Check if this is the case and manually adjust species level taxonomy for those cases (i.e., set the species level string to "GenusXY_speciesXY_var._XY")

Remove numeric characters and "-" in species level assignments


The code used to work on the 18S files is FixPEMAtaxassigments_18S_taxonomist.py, a python script which has comments and should be useable therefrom. Licence: CC BY SA.

The code used to work on the COI files is FixPEMAtaxassigments_COI_taxonomist.py, a python script which has comments and should be useable therefrom. Licence: CC BY SA.
