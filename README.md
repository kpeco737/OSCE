# OSCE Climate Assessment - Jupyter Notebook

This repository contains a Jupyter Notebook designed for exploring and comparing CORDEX model data and observational climate data (e.g., temperature, precipitation, wind) over Moldova. The notebook allows users to:
- Load observational data from CSV files.
- Load CORDEX model data (with bias-correction and unit conversion options).
- Visualize data through interactive plots (timeseries, PDFs with kernel density estimates, and boxplots, including monthly breakdowns).
- Apply quantile mapping bias correction to model data (except for wind).

## Prerequisites

- **Python 3.8** (or later; see the environment file for details)
- [Jupyter Notebook](https://jupyter.org/)
- A working installation of [Conda](https://docs.conda.io/en/latest/) or [pip](https://pip.pypa.io/en/stable/) to install dependencies.

## Installation

### Using Conda (Recommended)

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/kpeco737/OSCE.git
   cd your-repo-name

2. **Create & Activate the Environment**
- An environment file environment.yml is provided. Create the environment by running:

    conda env create -f environment.yml -n your_environment_name
    cond activate your_environment_name

- If you prefer pip, install the required packages from environment.txt by running

    pip install -r requirements.txt

3. **Running the Notebook**

- With your environment activated, start the notebook server:
    jupyter notebook

- Open the Notebook:
    In the Jupyter Notebook interface, locate and open the notebook file (OSCE_Climate_Assessment.ipynb).

- Interacting with the Notebook:
    **Model & Variable Selection:**
    Use the dropdown menus to choose the CORDEX model (GCM), the variable (e.g., Temperature, Precipitation, Wind), and the location.

    **Plot Type Options:**

        1. For Precipitation, only PDF and Boxplot options are available.
        2. For other variables, Timeseries, PDF, and Boxplot plots are available.

    - Additional Options:
        1. For Timeseries plots, you can toggle "Show Regression" to overlay a linear trend line.
        2. The "Apply Bias Correction" option is available for all variables except Wind.
        3. When Boxplot is selected, an additional dropdown ("Boxplot Frequency") allows you to choose between Annual and Monthly groupings.

    **Disclaimer for Wind:**
    If Wind is selected, a disclaimer will be printed stating that observational data are maximum daily gusts, while model data are daily averages.

**Data Requirements**
- Observational Data:
    Ensure that your observational CSV files are placed in the folder specified in the notebook (e.g., /Users/kpeco/Documents/GitHub/OSCE/Obs/Moldova). Change the 'obs_data_dir' variable to your own directory to read in the observational data. Each CSV should include separate columns for Years, Month, and Date (which are converted into a single datetime column).

- Locations Data:
    A CSV file named Moldova_locs.csv (with columns Location,Latitude,Longitude) must be available in the same folder as the observational data.

- CORDEX Model Data:
    The CORDEX data should be organized by GCM (e.g., MOHC-HadGem2, MPI-ESM-LR, NCC-Noresm1) with any subdirectories and filenames as specified in the notebook. Set the 'base_dir' argument in the load_cordex_data() function to your own directory where the CORDEX model data was saved.