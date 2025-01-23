The fasta files as output from PEMA processing for the second data release. 
Within these files, each row contains an identifier+the DNA sequence. This identifier is also used in the taxonomic assignment files, so you can match the information in these files in this way. Note that the date in the filename refers to the date of sequencing, rather than the date of the sampling event.

For COI:

The files called all_samples_xxx contain all the sequences inferred in all samples. The sequence identifiers are of the format ID;size=readAbundance. These are the input files for the clustering algorithm.
The files called all_sequences_grouped_xxx contain the sequences remaining after chimera removal and clustering. The sequence identifiers are of the format ID_readAbundance.
For 18S:

The files called final_all_samples_xxx contain all the sequences inferred in all samples. The sequence identifiers are of the format ID_readAbundance. These are the input files for the clustering algorithm.
The files called all_sequences_grouped_xxx contain contain the sequences remaining after chimera removal and clustering. The sequence identifiers are of the format OtuXY.
The files called Aligned_assignments_xxx contain clustered sequences which could be assigned to any taxonomic level. The sequence identifiers are of the format OtuXY Main genome; Eukaryota;etc.
For ITS:

The files called all_samples_xxx contain all the sequences inferred in all samples. The sequence identifiers are of the format ID;size=readAbundance. These are the input files for the clustering algorithm.
The files called all_sequences_grouped_xxx contain the sequences remaining after chimera removal and clustering. Because there was an error within PEMA at the time of usage regarding the sequence identifier format for ITS runs, the sequence identifiers in these files are of the format OtuXY. However, these sequences represent ASVs clustered with Swarm v2.
The files called Aligned_assignments_xxx contain clustered sequences which could be assigned to any taxonomic level. The sequence identifiers are of the format OtuXY Cellular organisms; Eukaryota;etc. Because of the previously mentioned error, the sequences are called OTUs, even though they represent ASVs clustered with Swarm v2.

The files are too large to store here in GitHub, so they have been placed in the Marine Data Archive for access. The download URL for these files are the following: