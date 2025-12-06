# Olfactory_mood_analysis
## Dataset Description
Used real olfactory datasets from the Pyrfume Project, which compiles validated chemical + perceptual data.
The two datasets:
1. Leffingwell Molecule Dataset
  Contains:
    * Molecule ID
    * Name
    * CAS number
    * Isomeric SMILES
    * Structural / physicochemical properties
    * Possibly aromatic category tags
2. Leffingwell Behavioral Dataset
  Contains:
    * Behavioral descriptors
    * Perceptual qualities: pleasantness, intensity, descriptors
    * Odor vocabulary
    * Links to the molecular ID
      
These datasets are widely used in computational olfaction research. They are absolutely real, peer-validated chemical/perceptual datasets.
In this project dataset (data.xlsx) is participant-level behavior ratings (e.g., pleasantness, intensity, familiarity, demographics).

## Dataset Modification
### A. Stimuli Modifications
  Function: modify_stimuli()
  ### Modifications Performed:
  1. Reset and rename index → molecule_id
    * Ensures a consistent key for merging datasets.
  2.Merge molecules with behavior descriptors
    * Combines chemistry + descriptive labels.
  3. Detect SMILES column automatically
    * Removes rows missing chemical structures.
  4. Drop duplicate molecules
    * Ensures one molecule = one unique stimulus.
### Why?
To create a clean, unified stimulus table containing:
  * molecular information
  * behavior descriptors
  * unique standard identifiers
This ensures merging with participant behavioral data works smoothly.
### B. Behavioral Dataset Modifications
Function: modify_behavior()
### Modifications Performed:
  1. Rename molcode or odor_id → molecule_id
    * Standardizes the merge key.
  2. Select rating column
    * Prefers 'pleasant'.
    * If missing, uses the first numeric column (failsafe).
  3. Drop rows missing ratings
    * Ensures valid dependent variables for analysis.
### Why?
Participant data from experiments must be aligned with stimulus IDs and must have complete ratings.
### C. Behavior + Stimuli Merge
Function: merger_behavior_stimuli()
### Modifications Performed:
  1. Unifies molecule_id types (string)
  2. Full merge of participant ratings with molecule features
  3. Drop rows missing SMILES (invalid chemucal structures)
### Why?
To produce a dataset where each row = participant* molecule, including
  * chemical features
  * molecular descriptors
  * participant ratings
  * 
This is the core dataset for modeling

