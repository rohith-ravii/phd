# Analysis of Lipid Bilayer Properties from Molecular Dynamics Simulations

This project contains a Jupyter Notebook (`lipid_properties.ipynb`) for analyzing molecular dynamics (MD) simulations of lipid bilayers. The notebook provides tools to calculate and visualize two key properties: bilayer thickness and deuterium order parameter (S_CD).

## Project Overview

The primary goal of this project is to offer a streamlined way to extract meaningful biophysical properties from raw MD simulation data. The notebook is structured to be interactive and easily adaptable for different simulation setups. It uses powerful libraries like `MDAnalysis` for handling simulation trajectories and `matplotlib` for generating publication-quality plots.

## Features

The notebook is divided into two main analysis sections:

1.  **Bilayer Thickness Calculation:**
    *   Calculates the thickness of the lipid bilayer across the simulation box.
    *   Works by identifying the phosphate groups in the upper and lower leaflets and measuring the distance between them.
    *   The results are binned into a 2D grid to create a thickness map.
    *   Generates a 2D heatmap visualizing the bilayer thickness.
    *   Outputs the raw thickness data to a `.dat` file.

2.  **Deuterium Order Parameter (S_CD) Calculation:**
    *   Calculates the S_CD order parameter for the lipid acyl chains, which is a measure of the conformational order of the lipid tails.
    *   The calculation is parallelized using Python's `multiprocessing` module to significantly speed up the analysis of long trajectories.
    *   Generates a 2D heatmap of the average S_CD values.
    *   Saves the S_CD map to a `.dat` file.

## Requirements

To run the notebook, you will need the following Python libraries:

*   `MDAnalysis`
*   `numpy`
*   `matplotlib`
*   `tqdm`
*   `ipywidgets` (for interactive elements in Jupyter)

You can install these packages using `pip` or `conda`. For example, with `conda`:

```bash
conda install -c conda-forge mdanalysis numpy matplotlib tqdm ipywidgets
```

## Usage

1.  **Clone or download the repository.**
2.  **Open the `lipid_properties.ipynb` notebook** in a Jupyter environment.
3.  **Update the file paths:** Before running the cells, you **must** update the hardcoded file paths in the notebook to point to your own simulation data files (e.g., `.gro`, `.xtc`, `.psf`). The paths are specified in the "User parameters" section of each analysis.

    *For example, in the bilayer thickness calculation, you need to change these lines:*
    ```python
    gro_file = "path/to/your/file.gro"
    xtc_file = "path/to/your/trajectory.xtc"
    ```

4.  **Run the cells:** Execute the cells in the notebook to perform the analysis and generate the plots.

## Input

The notebook expects standard MD simulation file formats:

*   **Topology/Structure file:** `.gro`, `.psf`, or any other format supported by `MDAnalysis`.
*   **Trajectory file:** `.xtc`, `.dcd`, or any other format supported by `MDAnalysis`.

## Output

The notebook generates two main types of output for each analysis:

*   **2D Heatmap Plots:** Visualizations of the calculated properties (bilayer thickness and S_CD) are displayed directly in the notebook.
*   **Data Files:** The raw data for the heatmaps is saved to text files (`thickness_map.dat` and `scd_map.dat`), which can be used for further analysis or plotting with other software.
