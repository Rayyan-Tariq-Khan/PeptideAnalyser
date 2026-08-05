# PeptideAnalyser

**Try the Colab version >** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Rayyan-Tariq-Khan/PeptideAnalyser/blob/main/PeptideAnalyser.ipynb)

This repository contains a python notebook for calculating biochemical properties of proteins or peptides from common proteomics file formats.

**1. Protein FASTA Analyzer**

Input-

input.fasta - containing protein sequences.
swissprot.tsv - (downloaded inside the notebook in the setup code block from Swiss-Prot).


Output-

File with one row per protein containing:

FASTA header
UniProt ID
Organism ID (if available)
Original sequence
Signal peptide present (Yes/No)
Signal peptide length
Trimmed (mature) sequence
Full protein:
Length
Molecular weight (Biopython)
GRAVY
pI
Amino acid frequencies
Mature protein (signal peptide removed, when annotated):
Length
Molecular weight
GRAVY
pI
Amino acid frequencies

Signal peptide annotations are obtained from the local swissprot.tsv file. If no annotation is present, only the full protein properties are reported.

**2. MaxQuant Peptide Analyser**

Input-
evidence.txt exported from MaxQuant (Uses only: Sequence, Proteins.)

Output -

File with one row per peptide containing:

Protein IDs
Peptide sequence
Length
Molecular weight
GRAVY
pI
Amino acid frequencies

Only the canonical peptide sequence is analyzed (no PTM or charge-state calculations).

**3. Spectronaut Peptide Analyser**

Input-

Spectronaut TSV export. It can be in any format as long as it has the following 2 columns- PG.ProteinGroups, EG.PrecursorId

Output-

File with one row per precursor containing:

Protein group(s)
Original precursor ID
Clean peptide sequence
Charge state
Detected PTMs
Number of PTMs
Unknown PTMs
PTM mass shift
Length
Canonical molecular weight
PTM-adjusted molecular weight
Theoretical precursor m/z
GRAVY
pI
Amino acid frequencies

The notebook also prints a summary of all detected PTMs and any unknown modifications encountered.

Notes
Molecular weight, GRAVY and pI are calculated using Biopython.
PTM-adjusted molecular weight is calculated by adding standard proteomics mass shifts to the canonical molecular weight.
GRAVY and pI are calculated from the canonical amino acid sequence (PTMs are not included in these calculations).
