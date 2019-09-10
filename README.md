# jupyterlab-info

### JupyterHub for Geohackweek 2019

During [Geohackweek 2019](https://geohackweek.github.io) we used a common computational environment running on Amazon Web Services: [https://nasa.pangeo.io](https://nasa.pangeo.io). This is a JupyterHub with a common Python environment to facilitate running tutorial contents. This repository has some information about the Hub, and a copy of the Python environment file in case you want to run things on your personal computer.

`nasa.pangeo.io` is running in the AWS region `us-east-1`. It is maintained by the [Pangeo project](http://pangeo.io) and is supported by [NASA Grant #17-ACCESS17-0003](https://github.com/pangeo-data/nasa-access-17) and cloud credits from Amazon. Access is currently limited to the [Geohackweek GitHub Organization](https://github.com/geohackweek). 


### Re-create the same JupyterLab environment on your personal computer

The Jupyter project has instructions for capturing the full Python environment from a Hub for re-use. See: https://mybinder.readthedocs.io/en/latest/tutorials/reproducibility.html

Run the following code to re-create the environment locally:

**1) Install miniconda if you don't have it already**
```
https://docs.conda.io/en/latest/miniconda.html
```

**2) Create a conda environment**
```
conda env create -f environment.yml
```

**3) Activate the environment and install JupyterLab extensions**
```
conda activate geohackweek2019
jupyter labextension install @jupyter-widgets/jupyterlab-manager \
				@jupyterlab/geojson-extension \
				@pyviz/jupyterlab_pyviz \
				jupyter-matplotlib \
				jupyter-leaflet \
				dask-labextension
```

**4) Launch JupyterLab**
```
jupyter lab
```

### Frequently Asked Questions (FAQs)

##### Why run on AWS? 

There are some big advantages to using a common JupyterHub. Everyone has access to ephemeral computational resources, so you are not limited by your laptop CPU and RAM. We can also easily share large amounts of data. For example, everyone on the hub has read-write access to `s3://geohackweek2019`. 

##### I'm getting errors trying to install the environment on a mac

There are sometimes incompatibilities with conda packages on linux versus osx. 

For example, the following are linux-specific and therefore won't install on a mac
```
ResolvePackageNotFound:
  - libgfortran-ng=7.3.0
  - libstdcxx-ng=7.3.0
  - libgcc-ng=7.3.0
```

Solution: Comment out those lines in `environment.yml` with the `#` character.

##### Can I do this with Docker

Instead of installing miniconda and creating a new conda environment, you can use a Docker image that has everything pre-installed. This is helpful for running the hub in a different Cloud provider region. See https://cloud.docker.com/u/scottyhq/repository/docker/scottyhq/geohackweek2019

`docker pull scottyhq/geohackweek2019:2019-08-01`


##### Can I run this as a Jupyter Binder?

Yes! The buttons below will pull the docker image and spin up an environment where you can run tutorials (WARNING: your home directory will not persist)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geohackweek/jupyterlab-info/master?urlpath=lab)

# Launch on Pangeo Binder

[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=Pangeo+Binder&message=GCE+us-central1&color=blue)](https://binder.pangeo.io/v2/gh/scottyhq/geohackweek/jupyterlab-info/master?urlpath=lab)

[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=Pangeo+Binder&message=AWS+us-west-2&color=orange)](https://aws-uswest2-binder.pangeo.io/v2/gh/geohackweek/jupyterlab-info/master?urlpath=lab)

