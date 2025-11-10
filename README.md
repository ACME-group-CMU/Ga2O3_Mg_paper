# First Principles Study of Mg-Induced Phase Stabilization in Ga<sub>2</sub>O<sub>3</sub> Polymorphs

## File description:
### Notebooks
	Supercell_Generator.ipynb   
		- Generates cubic and oriented supercells from the primitive cell.  
		- Corresponds to Computational Details.  
	SubsStructGen.ipynb   
		- Generates Mg-substituted structures from the supercell, checks for structural equivalence, and outputs a sample of structures with the lowest weighted-average KL divergence.  
		- Corresponds to Computational Details and Supporting Information: Selection of Representative Subset of Alloy Structures.  
	INPfile_generator.ipynb   
		- Generates Quantum ESPRESSO input (.in) files for the selected sample of structures.  
		- Produces inputs used in the DFT runs described in the Methods section.  
	Graphing_DFT_Ga2O3.ipynb   
		- Generates figures and plots from the DFT results (energy comparisons, structural metrics, etc.).  
		- Corresponds to Results and Figures in the paper.  
### Other files
	Mg-Ga2O3_Dependencies.yaml - conda environment containing all dependencies  
	substituted structures.zip - compressed folder containing .cif structure files and QE input files for all substituted structures used in study

## Reproducing results:
### Prerequisites
  `git` 
  `conda`  
  `Jupyter Notebook`  
  `Quantum ESPRESSO`  

  1) Clone the repository  
	    `git clone https://github.com/ACME-group-CMU/Ga2O3_Mg_paper.git  
		cd Ga2O3_Mg_paper`

  2) Create and activate a conda environment using Mg-Ga2O3_Dependencies.yaml  
	    `conda env create -f Mg-Ga2O3_Dependencies.yaml 
	    conda activate MgGa2O3`

  3) Create a Jupyter kernel for the environment  
	   ` python -m ipykernel install --user --name MgGa2O3 --display-name "MgGa2O3 (Python)"`

  4) Run notebooks in the following order (ensure required changes to file paths in the code are made)  
	    A) Supercell_Generator.ipynb  
		      - Output: supercell structure files.  
	    B) SubStructGen.ipynb  
		      - Output: selected substituted structures  
	    C) INPfile_generator.ipynb  
		      - Output: QE .in files  

  5) Use input files to run DFT calculations on Quantum ESPRESSO  
	    Use the generated QE input files to run pw.x or your cluster workflow. Make sure pseudopotentials and paths referenced 	by the .in files are correct.  

## Citation  
  If you use this code or reproduce the results in your own work, please cite:  
