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
