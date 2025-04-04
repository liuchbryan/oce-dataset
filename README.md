# Datasets for Online Controlled Experiments

This is a project in two parts:
1. The first survey and taxonomy for existing online controlled experiment datasets, and
2. The ASOS Digital Experiments dataset - the first public dataset that supports the design and running of experiments with adaptive stopping.

The work is accepted into NeurIPS 2021 Track on Datasets and Benchmarks. (Link to [NeurIPS proceedings](https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/hash/274ad4786c3abca69fa097b85867d9a4-Abstract-round2.html) | [OpenReview](https://openreview.net/forum?id=79shW3z5Eaq) | [arXiv](https://arxiv.org/abs/2111.10198))

If you find the project helpful, please use the following citation:
```
@inproceedings{liu2021datasets,
 author = {Liu, C. H. Bryan and Cardoso, \^{A}ngelo and Couturier, Paul and McCoy, Emma J.},
 booktitle = {Proceedings of the Neural Information Processing Systems Track on Datasets and Benchmarks},
 editor = {J. Vanschoren and S. Yeung},
 pages = {},
 title = {Datasets for Online Controlled Experiments},
 url = {https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/file/274ad4786c3abca69fa097b85867d9a4-Paper-round2.pdf},
 volume = {1},
 year = {2021}
}
```

# Survey of existing OCE datasets

A summary of the survey, together with the direct links to the datasets are available on this [Open Data StackExchange answer](https://opendata.stackexchange.com/a/20117/30576).


# Experimenting with the ASOS Digital Experiments Dataset

## Loading the ASOS Digital Experiments dataset

The dataset is available on: https://osf.io/64jsb/ .

The experiment notebook uses the parquet form of the dataset. It would attempt to download the file before getting pandas to load the dataframe. If that doesn't work, you can either:

To get the parquet form of the dataset used in the experiments, you can do one of:
* Download the file via [this direct link](https://osf.io/62t7f/download) and place it in the `data` directory, or
* Use the following command at the root of this repo:
  ```
  wget -O ./data/asos_digital_experiments_dataset.parquet https://osf.io/62t7f/download
  ```

## Setup
This file assumes you have access to a \*nix-like machine (both MacOS or
Linux would do). If you have a Windows machine, the notebook should still work
provided you have the right Python packages installed, but it is not tested.

This project uses `pyenv` and `poetry` for package management.
Before you start, please ensure you have `gcc`, `make`, and `pip` installed.

### Installing `pyenv`

For Linux (together with other required libraries):

``` bash
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
wget -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

chmod u+x pyenv-installer
./pyenv-installer
```

For OS X:
```
brew install pyenv
brew install pyenv-virtualenv
```

We then need to configure the PATHs:
```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

...and install the right Python version for our environment:
```
pyenv install 3.12.9
```

### Installing `poetry`
See https://python-poetry.org/docs/#installation for the installation instructions.

### Download the repository and sync the environment
```
git clone https://github.com/liuchbryan/oce-dataset.git
cd oce-dataset  

# Switch to Python 3.12.9 for pyenv
poetry env use ~/.pyenv/versions/3.12.9/bin/python
poetry install
```

### Run the Jupyter notebooks  
```
poetry shell
```

Within the newly spawn up virtualenv shell, run
```
jupyter notebook
```

Once you are done, terminate the Jupyter server using Ctrl+C, and type `exit` to exit the virtualenv shell.  
