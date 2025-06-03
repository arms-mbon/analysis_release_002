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

| filename | download URL | 
| --- | --- |
| all_samples_April2021_COI.fasta| [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05027a376824969](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05027a376824969) |
| all_samples_August2023_COI.fasta| [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf050335366339328](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf050335366339328) |
| all_samples_September2020_COI.fasta| [	https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05037e863856014](	https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05037e863856014) |
| all_sequences_grouped_April2021_COI.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf0523bd985666107](	https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf0523bd985666107) |
| all_sequences_grouped_August2023_COI.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05038e304477491](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ddf05038e304477491) |
| all_sequences_grouped_September2020_COI.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ec58b6c4d489886842](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836ec58b6c4d489886842) |
| Aligned_assignments_April2021_ITS.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1baf206164086](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1baf206164086) |
| Aligned_assignments_September2020_ITS.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1b74403284481](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1b74403284481) |
| all_samples_April2021_ITS.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1c7b504652556](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1c7b504652556) |
| all_samples_September2020_ITS.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1b35458380398](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1b35458380398) |
| all_sequences_grouped_April2021_ITS.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1e4d332893135](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1e4d332893135) |
| all_sequences_grouped_September2020_ITS.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1d15598077194](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e1efe1d15598077194) |
| Aligned_assignments_April2021_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad4d41893285473](	https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad4d41893285473) |
| Aligned_assignments_August2023_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fcf4378071514](		https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fcf4378071514) |
| Aligned_assignments_September2020_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ae1bae728553767](		https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ae1bae728553767) |
| all_samples_April2021_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ae082c389859723](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ae082c389859723) |
| all_samples_August2023_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc6d308577778](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc6d308577778) |
| all_samples_September2020_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad0c20148218511](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad0c20148218511) |
| all_sequences_grouped_April2021_18S.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad8ee3628405491](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad8ee3628405491) |
| all_sequences_grouped_August2023_18S.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc0e672993879](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc0e672993879) |
| all_sequences_grouped_September2020_18S.fa | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9adcd6f622432834](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9adcd6f622432834) |
| final_all_samples_April2021_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad17c5633110787](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad17c5633110787) |
| final_all_samples_August2023_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc20023411188](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836e9574fc20023411188) |
| final_all_samples_September2020_18S.fasta | [https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad4b9c562208171](https://mda.vliz.be/directlink.php?fid=VLIZ_00001620_6836eb9ad4b9c562208171) |
