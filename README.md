# First Principles Study of Mg-Induced Phase Stabilization in Ga<sub>2</sub>O<sub>3</sub> Polymorphs

This repository contains files and environment specification to reproduce results contained in the paper (link forthcoming) of the same title as this README file.

## File description:
### Notebooks
- `Supercell_Generator.ipynb`   
	- Generates cubic and oriented supercells from the primitive cell.  
	- Corresponds to Computational Details.  
- `SubsStructGen.ipynb`
	- Generates Mg-substituted structures from the supercell, checks for structural equivalence, and outputs a sample of structures with the lowest weighted-average KL divergence.  
	- Corresponds to Computational Details and Supporting Information: Selection of Representative Subset of Alloy Structures.  
- `INPfile_generator.ipynb`
	- Generates Quantum ESPRESSO input (.in) files for the selected sample of structures.  
	- Produces inputs used in the DFT runs described in the Methods section.  
- `Graphing_DFT_Ga2O3.ipynb`
	- Generates figures and plots from the DFT results (energy comparisons, structural metrics, etc.).  
	- Corresponds to Results and Figures in the paper.  
### Other files
- `environment.yml` - conda environment file, instructions to build environment below
- `substituted structures.zip` - compressed folder containing .cif structure files and QE input files for all substituted structures used in study

## Reproducing results:
### Prerequisites
- bash, zsh, or similar terminal environment
- git
- conda
- access Quantum ESPRESSO in an HPC environment

### Steps  
1) Clone the repository and enter the directory:
	```
	git clone https://github.com/ACME-group-CMU/Ga2O3_Mg_paper.git  
	cd Ga2O3_Mg_paper
	```

2) Create and activate a conda environment with requisite dependencies:
	```
	conda env create -f environment.yml 
	conda activate MgGa2O3
	```

3) Create a Jupyter kernel for the environment:
	```
	python -m ipykernel install --user --name MgGa2O3 --display-name "MgGa2O3 (Python)"
	```
	
4) Now, to open any given notebook, you can simply run (e.g. for the first one) `jupyter notebook Supercell_Generator.ipynb` and the kernel you created should appear in the dropdown menu as an option.

5) Run the notebooks in the following order (ensure required changes to file paths in the code are made)  
	- `Supercell_Generator.ipynb`: outputs supercell structure files
	- `SubStructGen.ipynb`: outputs selected substituted structures  
	- `INPfile_generator.ipynb`: generates QE `.in` files

6) Use input files to run DFT calculations on Quantum ESPRESSO via `pw.x` or your cluster workflow. Make sure pseudopotentials and paths referenced in the `.in` files are correct for your QE setup.

7) Finally, the `Graphing_DFT_Ga2O3.ipynb` notebook will generate the plots shown in the paper (including SI figures).

## Citation  
  If you use this code or reproduce the results in your own work, please cite:  
