# analysis_release_002

These are the PEMA input/output files representing the source data for the second ARMS-MBON dataset submitted to (Eur)OBIS (see the README in [data_release_002](https://github.com/arms-mbon/data_release_002) for an explanation of the source data): count and taxonomy tables, fasta files, and PEMA parameter files for the COI, 18S, and ITS marker gene sequence data for the events of ARMS-MBON's second sampling campaign (i.e. samples from all ARMS deployed in 2020 and 2021 and retrieved between and 2020 and 2021).  

[PEMA](https://github.com/hariszaf/pema) is the metabarcoding analysis pipeline we use to process the COI, 18S, and ITS raw sequence data obtained from the ARMS-MBON samples. 

The raw sequences are deposted in [ENA](https://www.ebi.ac.uk/ena/browser/home). Information on metadata regarding these can be found in [the data workspace repo](https://github.com/arms-mbon/data_workspace/tree/main/qualitycontrolled_data) and on protocols on how sequences were generated can be found in [SOPs](https://github.com/arms-mbon/documentation/tree/main/standard_operating_procedures). 

The sequence data were processed separately for marker genes and MiSeq sequencing runs with the metabarcoding pipeline [PEMA](https://github.com/hariszaf/pema). Included in this repository are:
* The parameter files used as input for each PEMA processing run
* The read count and taxonomic assignment files output by PEMA
* The fasta files output by PEMA

PEMA was marker genes and MiSeq sequencing runs, and each PEMA run therefore has its own parameter, read count, taxonomic assignment, and fasta files. An overview of the processing - including the material sample IDs, ENA accession numbers, deployment dates and corresponding observatories etc. - from which one can identify which samples were processed in which group, is provided in *ADD LINK*

The full set of PEMA files (i.e., for all the ARMS-MBON processing we have done) can be found in [ARMS GitHub working space](https://github.com/arms-mbon/data_workspace/tree/main/analysis_data/from_pema). This analysis_release_002 repository is specifically the subset of those results representing [processing_batch2](https://github.com/arms-mbon/data_workspace/tree/main/analysis_data/from_pema/processing_batch2).

Note that the code used to analyse the taxonomic outputs of PEMA for this second data release can be found in (code_release_002)[https://github.com/arms-mbon/code_release_002).

Some of the PEMA processing metadata for the runs performed here. Further information can be found in the manuscript associated with data_release_002 and via the PEMA URL:
| parameter | value |
| --- | --- | 
| PEMA URL | https://github.com/hariszaf/pema | 
| PEMA version | v2.1.4 | 
| ref database for taxonomy assignment | Midori v2.0 (COI),  PR2 v.4.13.0 (18S), Unite v7.2 (ITS)| 
| clustering algorithm | Swarm v2 (COI, ITS), VSEARCH v2.9.1 (18S) | 




