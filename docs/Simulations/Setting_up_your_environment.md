## Prelims
First, let's install a common command line environment.

On windows install the terminal app and Ubuntu from the windows store.  Installing Ubuntu should also install WSL (Windows Subsystem for Linux) and then a full virtual machine installation of Ubuntu 24.04, a Linux distribution.  Once complete, open the terminal app and from the drop down, select Ubuntu.  You may also want to go to the terminal settings and make Ubuntu the default, so it opens automatically upon installing terminal.

On MacOS, there is a terminal app installed by default.  MacOS has a linux like core, and all the usual linux commands (mkdir, cd, ls, grep...) also work on the MacOS command line.

## Installing miniconda (python + conda package manager)

At the commandline, download the latest version of miniconda.

```
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh | bash
```
```
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh | bash
```

Generally the defaults for the installation are fine, and choose yes at the end to update your .bashrc file so that the conda environment loads automatically when you open the terminal.  If it's setup correctly, you should see the text "(base)" at the start of your commandline.  This means conda is loaded and you are currently in the base environment.  Let's get any updates available.

```
conda update conda 
conda update -–all
```

## Making a new environment for installing packages

Although conda is designed to help python packages work together well, the more packages you install, the greater chance of conflicts, so it's advisable to keep the base environment fairly pristine, and to create new environments before installing a new collection of packages.  This also allows you to set the python version per environment. Packages get updated at different rates, so you will often have to go back several python versions to get to a version where all your packages can work together.

As of June, 2026, miniconda ships with python version 3.13, but you will likely need to go back a few versions (3.12, 3.11, 3.10..) until you find a version that works with all your desired packages.

Let's create an environment called "md" for our computational chemistry tools, and then switch to it.

```
conda create -n md python=3.12
conda activate md
```
You should now see "(md)" instead of "(base)" as part of your commandline.

Let's try installing the majority of our packages (This might take a while to solve the environment):

```
conda install -c conda-forge rdkit biopython openmm openmm-setup mdtraj parmed openbabel pymol-open-source spyder datamol ase nglview xtb xtb-python psi4 dftd3-python dftd4-python pdbfixer openff-toolkit py3dmol jupyterlab nglview ipywidgets ambertools MDAnalysis
```

There's also one package that is quite useful, but is not found in the conda package repositories, so we'll install it with pip.

```
pip install molify
```

If all installs sucessfully, you should now be ready to run any of the scripts or notebooks found in these docs.  Generally when starting a new session, open the terminal, and activate the md enviornment (conda activate md).

## Testing
Test a few tools installed through conda, and verify the following commands work:

| Command/program  | Purpose                                       |
| ---------------- | --------------------------------------------- |
| Spyder           | code editor and development environment       |
| jupyter lab      | jupyter notebooks (opens in a browser tab)    |
| pymol            | molecule viewer/visualizer/light editor       |

Some additional tools that can be useful to install or have bookmarked.

Avogadro 2 - Builder/Optimizer for small to medium systems: https://avogadro.cc/install/index.html

Chemistry Line Structure Editor / Viewer - https://app.molview.com/

Visual Molecular Dynamics (VMD) - https://www.ks.uiuc.edu/Research/vmd/

Orca quantum package - https://orcaforum.kofo.mpg.de/index.php

Amber Moleculer Dynamics - https://ambermd.org/



