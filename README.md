# Structural and Sequence Similarity Search against MIBiG

This repository implements two similarity search techniques for bioinformatics:
  - **Structural Similarity Search**: Perform structural similarity comparisons between molecules. It calulates the [MAP4](https://github.com/reymond-group/map4) fingerprint from a SMILES string of a given input molecule and calculates the Jaccard distance to molecules found in the MIBiG database
  - **Protein Sequence Similarity Search**: Uses [blastp](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-10-421) to compare protein sequences against the MIBiG database, enabling the identification of biologically relevant homologs.

Both methods aim to assist in the analysis and discovery of structurally and functionally similar compounds and protein sequences. For easy use of the code the jupyter notebook are implemented in binder. You can use it by clicking the badget below:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/phillipschl/MIBiG_similarity_search.git/HEAD)

## Structural Similarity Search
### Usage

This repo contains two jupyter notebooks:
  - `calculate_dist.ipynb`: notebook to calculate similarities against the MIBiG database. After defining the input SMILES and output file name hit `Run` > `Run all`. 
  - `draw_structures.ipynb`: additional notebook to draw the molecules from the output `csv` file from `calculate_dist.ipynb`. Just define the filename of the output `csv` and run the cells. The output will be a grid view with the molecular structures annotated by the MIBiG accesion ID and the calculated Jaccard distance.

### Output

The `calculate_dist.ipynb` notebook outputs a table with all sorts of information to the given molecule:

  - `loci_accession`: NCBI accesion number
  - `loci_end_coord` and `loci_start_coord`: end and start position of the BGC inside the accession
  - `mibig_accession`: mibig accession number
  - `ncbi_tax_id`: NCBI taxanomy ID
  - `organism_name`: organism name
  - `publications`: ID to respective publication
  - `smiles`: SMILES string of the molecule
  - `MAP4`: MAP4 fingerprint
  - `fcsp3`: fraction of C atoms that are SP3 hybridized
  - `HBA`: number of H-bond acceptors
  - `HBD`: number of H-bond donors
  - `MW`: molecular weight in g/mol
  - `isLipinski`: wheter the molecule satisfies the Lipinski rule of 5
  - `isPeptide`: wheter the molecule is a peptide
  - `hasSugar`: wheter the molecule has a sugar moiety
  - `distance`: calculated Jaccard distance

## Protein Sequence Similarity Search

This tool implemented in the `blastp.ipynb` notebook performs a protein sequence similarity search by comparing a query protein sequence against the MIBiG database to identify homologous proteins. 

### Usage

To use the similarity search tools, open the `blast.ipynb`:
  1. Upload your query protein sequence in FASTA format by simply dragging and dropping the file into the file browser.
  2. Define the input parameters for the search, such as the similarity thresholds and database options.
  3. Run the search to perform the structural similarity comparison using the protein sequence similarity search with blastp against the MIBiG database.

## Output

The notebook produces three output files: a tabular `csv` file containing general information about the similarity hits, a sorted `csv` file (by sequnce identity), and a `txt` file containing the sequence alignment which can be imported to your alignment viewer of coice (e.g. [MPI toolkit](https://toolkit.tuebingen.mpg.de/tools/alnviz)). The tabular output `csv` contains the following information:
  - `query_id`: query or source (gene) sequence id
  - `subject_id`: contains information of the BGC, including MIBiG and NCBI accesion ID, as well as the gene identifier
  - `percent_identity`: percentage of identical positions
  - `alignment_length`: alignment length (sequence overlap)
  - `mismatches`: number of mismatches
  - `gap_opens`: number of gap openings
  - `q_start`: start of alignment in query
  - `q_end`: end of alignment in query
  - `s_start`: start of alignment in subject
  - `s_end`: end of alignment in subject
  - `e_value`: expect value, is the number of expected hits of similar quality (score) that could be found just by chance (the smaller the E-value, the better the match)
  - `bit_score`: bit score, in an alignment is a measure of the quality of the alignment between two sequences (the higher the bit-score, the better the sequence similarity)
