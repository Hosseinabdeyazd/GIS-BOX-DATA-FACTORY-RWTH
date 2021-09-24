# GIS-Box: Data Factory
cloned from Example Profile for RWTH Jupyter Hub cluster

![gisbox.jpg](./img/rheinisches-revier-neu.jpg)

## Introduction

This repository contains a Jupyter profile which works with the RWTHjupyter cluster. To be more specific, it includes the following files

* `Quickstart.ipynb` which is an exemplary Jupyter notebook file.
* `environment.yml` which specifies the required Python packages needed to run `Quickstart.ipynb`. This file is used by Anaconda or `conda`.
* `Dockerfile` which defines the linux environment. In the end, the packages in `environment.yml` are installed.
* `.gitlab-ci.yml` which specifies the necessary Docker build commands (which are executed every time `Dockerfile` changes in Git).
* `.gitlab-ci.yml` which specifies the necessary Docker build commands (which are executed every time `Dockerfile` changes in Git).

## Installation

### Installation on RWTHjupyter cluster

Please follow the instruction listed here: https://jupyter.pages.rwth-aachen.de/documentation/instructors/NewProfiles.html

### Docker

If you happen to have Docker installed, you can start a local dockerized JupyterLab for testing your profile:

```bash
# Navigate to your local clone of this repo
#  Note: Adjust this path to your local environment
WORKDIR=/home/stv0g/example-profile

cd ${WORKDIR}

# Login to the RWTH GitLab Docker registry
#  (required for pulling the base image)
docker login registry.git.rwth-aachen.de

# Build the Docker image
docker build --tag jupyter-example-profile .

# Run the Docker image
docker run --name='jupyter-example-profile' --rm --interactive --tty --publish 8888:8888 --volume ${WORKDIR}:/home/jovyan jupyter-example-profile
```

Copy and paste the displayed link to your favorite browser.

### Local Installation

To run the notebooks on your local machine, you may use [Anaconda](https://www.anaconda.com/) (using `pip` is also possible for experienced users. You have to install all the requirements listed in `environment.yml` and install the commands listed in `postBuild.sh`).

* Install [Anaconda](https://www.anaconda.com/).
* Download this repository to your local disk. You can download it as a zip-File or use `git`:  

  ```bash
  git clone git@git-ce.rwth-aachen.de:jupyter/profiles/example.git
  ```

* It is highly recommended to run the notebooks in an isolated Anaconda environment. You can create a new environment called `jupyter-example-profile` from the provided `environment.yml` by running the following command in the Anaconda prompt

  ```bash
  conda env create -f environment.yml
  ```
  
  This makes sure that all required packages are installed amd don't interfere with the packages in your base environment.
* Activate this environment with

  ```bash
  conda activate jupyter-example-profile
  ```

### Local Run

* Activate the environment  with `conda activate jupyter-example-profile`.
* Run JupyterLab  `jupyter lab`. In your browser, JupyterLab should start. You can then open `index.ipynb` for an overview over all notebooks.
* You can deactivate the environment with `conda deactivate`.

## Contact

* If you found a bug, please use the [issue tracker](https://git-ce.rwth-aachen.de/jupyter/profiles/examples/issues).
* In all other cases, please contact [Christian Rohlfing](http://www.ient.rwth-aachen.de/cms/c_rohlfing/).

The code is licensed under the [MIT license](https://opensource.org/licenses/MIT).
