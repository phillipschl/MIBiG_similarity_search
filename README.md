# Similarity search against the MIBiG database

This repo is a tool to search for similar secondary metabolites against the [MIBiG (Minimum Information about a Biosynthetic Gene cluster)](https://mibig.secondarymetabolites.org/) database. The tool calculates the [MAP4](https://github.com/reymond-group/map4) molecular fingerprint from a SMILES string of a given input molecule and calculates the Jaccard distance to molecules found in the MIBiG database.
To use the code immediatly use jupyter notebook implemented in binder by clicking the badget below.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/phillipschl/MIBiG_similarity_search.git/HEAD)

## Usage

This repo contains two jupyter notebooks:
  - `calculate_dist.ipynb`: notebook to calculate similarities against the MIBiG database. After defining the input SMILES and output file name hit `Run` > `Run all`. 
  - `draw_structures.ipynb`: additional notebook to draw the molecules from the output `csv` file from `calculate_dist.ipynb`. Just define the filename of the output `csv` and run the cells. The output will be a grid view with the molecular structures annotated by the MIBiG accesion ID and the calculated Jaccard distance.

## Output ## 

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
