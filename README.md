# This a simple cheminformatics practice project.

## What did I do?

I took five familiar drug molecules (Aspirin, Ibuprofen, Naproxen, Diclofenac, and Paracetamol), pulled their structures from PubChem as SMILES strings, and asked a basic question:

**How similar are these molecules according to a computer?**

I calculated:
- Basic physicochemical properties (molecular weight, logP, hydrogen bond donors and acceptors)
- Morgan fingerprints (ECFP4)
- Pairwise Tanimoto similarity scores between all molecules

**Main finding:**  
Ibuprofen and Naproxen are clearly more similar to each other (Tanimoto = 0.42) than any other pair. This makes sense chemically — they both share the same 2-arylpropanoic acid core. All other pairs sit in a low similarity range (around 0.13–0.22).

Paracetamol (the non-NSAID) did not stand out as an outlier, which was a useful lesson: structural similarity alone does not tell you drug class.

## Why did I do it?

I am currently learning bioinformatics and cheminformatics.  
I wanted to move beyond tutorials and actually build one complete, end-to-end pipeline myself — from raw text (SMILES) all the way to a similarity matrix — so I could understand every decision along the way.

This project helped me learn:
- How SMILES strings work
- How RDKit turns text into molecular graphs
- What molecular fingerprints actually represent
- How Tanimoto similarity is calculated
- Why low similarity scores are often the expected result, not a failure

## How did I do it?

**Tools used:**
- Python
- RDKit
- pubchempy (to fetch structures from PubChem)
- pandas

**Pipeline:**

1. Fetch SMILES strings from PubChem by drug name
2. Convert SMILES → RDKit molecule objects
3. Calculate Lipinski descriptors (MW, logP, HBD, HBA)
4. Generate 2048-bit Morgan fingerprints (radius = 2)
5. Compute pairwise Tanimoto similarity

**Key result:**
- Strongest pair → Ibuprofen & Naproxen (0.42)
- Median similarity across all pairs → 0.19

All five molecules comfortably pass the Lipinski Rule of Five.
