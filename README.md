# Datasets for Online Controlled Experiments

This is a project in two parts:
1. The first survey and taxonomy for existing online controlled experiment datasets, and
2. The ASOS Digital Experiments dataset - the first public dataset that supports the design and running of experiments with adaptive stopping.

The work is accepted into NeurIPS 2021 Track on Datasets and Benchmarks. (Link to [NeurIPS pre-proceedings](https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/hash/274ad4786c3abca69fa097b85867d9a4-Abstract-round2.html) | [OpenReview](https://openreview.net/forum?id=79shW3z5Eaq) | [arXiv](https://arxiv.org/abs/2111.10198))

If you find the project helpful, please use the following citation while we wait for NeurIPS to finalise the bibtex:
```
@misc{liu2021datasets,
      title={Datasets for Online Controlled Experiments}, 
      author={C. H. Bryan Liu and Ângelo Cardoso and Paul Couturier and Emma J. McCoy},
      year={2021},
      eprint={2111.10198},
      archivePrefix={arXiv},
      primaryClass={stat.AP}
}
```

# Survey of existing OCE datasets

A summary of the survey, together with the direct links to the datasets are available on this [Open Data StackExchange answer](https://opendata.stackexchange.com/a/20117/30576).


# Experimenting with the ASOS Digital Experiments Dataset

## Loading the ASOS Digital Experiments dataset

The dataset is available on: https://osf.io/64jsb/

The notebook in this repo uses the parquet form of the dataset. Download the `*.parquet` file ([direct link](https://osf.io/62t7f/download)) and place it in the `data` directory.

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
pyenv install 3.8.1
```

### Installing `poetry`
See https://python-poetry.org/docs/#installation for the installation instructions.

### Download the repository and sync the environment
```
git clone https://github.com/liuchbryan/oce-dataset.git
cd oce-dataset  

# Switch to Python 3.8.1 for pyenv
pyenv local 3.8.1
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
