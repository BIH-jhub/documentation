
# Documentation

This is the user-documentation of the JupyterHub instance at [https://jhub.bihealth.org](https://jhub.bihealth.org).

## JupyterHub Custom Conda Environment Setup

This guide describes how to set up and use a custom conda environment. Why use a custom conda environment?

- Install specific package versions for reproducibility
- Access additional scientific packages from `conda-forge` and `bioconda`
- Isolate your work from the default environment

### 1. Initialize Conda (if needed)

```bash
conda init
/bin/bash
```

### 2. Configure Conda channels and environment directory

Create a `.condarc` file with the following content (e.g. by typing `vi .condarc` in the terminal):

```yaml
envs_dirs:
  - /home/jovyan/conda_envs/
```

### 3. Create an environment YAML file

Example `myenv.yaml`:

```yaml
name: myenv
channels:
  - conda-forge
  - bioconda
dependencies:
  - python=3.13.5
  - scipy=1.16.1
  - ipykernel=6.30.1
```

### 4. Create and activate the environment

```bash
conda env create -f myenv.yaml
conda activate myenv
```

### 5. Register the environment as a Jupyter kernel

```bash
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
```
