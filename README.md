# Brieflow Analysis Template

Template repository for analyzing optical pooled screens data using [Brieflow](https://github.com/cheeseman-lab/brieflow).

## Overview

This template provides a standardized structure for analyzing optical pooled screens using Brieflow. The key principle is:
- Core processing logic and code lives in the Brieflow package
- Analysis-specific workflows and rules live in this repository

## Prerequisites

1. Install Brieflow following [installation instructions](https://github.com/cheeseman-lab/brieflow#set-up-workflowconfiguration-conda-environments)
2. Set up the required conda environments as described in the Brieflow documentation

## Customizing for Your Screen

1. Fork this template repository

2. Core Processing Logic:
   - Any modifications to core processing functions should be made in the Brieflow package
   - Submit these changes via pull requests to Brieflow

3. Screen-Specific Logic:
   - Modify rules and targets in the workflow/ directory to customize for your screen
   - These changes stay in your forked analysis repository

### Analysis Steps

Follow the instructions below to configure parameters and run modules.
All of these steps are done in the analysis folder, but parameters that need to be filled out are blank.
These steps are equivalent to what is presented for the example analysis in [Brieflow](https://github.com/cheeseman-lab/brieflow).
Use the following command to enter this folder: `cd analysis/`. 

Deposit the data from your screen into a subfolder in `analysis/`

#### Step 0: Configure preprocess params

Follow the steps in [0.configure_preprocess_params.ipynb](analysis/0.configure_preprocess_params.ipynb) to configure preprocess params.

#### Step 1: Run preprocessing module

**Local**:
```sh
conda activate brieflow_workflows
sh 1.run_preprocessing.sh
```
**Slurm**:
```sh
sbatch 1.run_preprocessing_slurm.sh
```

***Note**: For testing purposes, users may only have generated sbs or phenotype images.
It is possible to test only SBS/phenotype preprocessing in this notebook.
See notebook instructions for more details.

#### Step 2: Configure SBS process params

Follow the steps in [2.configure_sbs_process_params.ipynb](analysis/2.configure_sbs_process_params.ipynb) to configure SBS process params.


#### Step 3: Configure phenotype process params

Follow the steps in  [3.configure_phenotype_process_params.ipynb](analysis/3.configure_phenotype_process_params.ipynb) to configure phenotype process params.

#### Step 4: Run SBS/phenotype process module

**Local**:
```sh
conda activate brieflow_workflows
sh 4.run_sbs_phenotype_processes.sh
```
**Slurm**:
```sh
sbatch 4.run_sbs_phenotype_processes_slurm.sh
```

***Note**: Use `brieflow_configuration` Conda environment for each configuration notebook.

***Note**: Many users will want to only run SBS or phenotype processing, independently.
It is possible to restrict the SBS/phenotype processing with the following:
1) If either of the sample dataframes defined in [0.configure_preprocess_params.ipynb](analysis/0.configure_preprocess_params.ipynb) are empty then no samples will be processed.
See the notebook for more details.
2) By varying the tags in the `4.run_sbs_phenotype_processing` sh files (`--until all_sbs_process` or `--until all_phenotype_process`), the analysis will only run only the analysis of interest.

### Run Entire Analysis

If all parameter configurations are known for the entire Brieflow pipeline, it is possible to run the entire pipeline with the following:

```sh
conda activate brieflow_workflows
sh run_entire_analysis.sh
sbatch run_entire_analysis.sh
```

## Contributing

- Core improvements should be contributed back to Brieflow
- Screen-specific modifications should remain in your forked analysis repository
- If you have analyzed any of your optical pooled screening data using brieflow-analysis, please reach out and we will include you in the table below!

## Examples of brieflow-analysis usage:

| Study | Description | Analysis Repository | Publication |
|-------|-------------|---------------------|-------------|
| _Coming soon_ | | | |