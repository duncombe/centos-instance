
# Setting up a python environment

Taken from Unidata Python workshop, to be modified for compliance checker, system-test.

```
git clone https://github.com/Unidata/unidata-python-workshop

conda config --add channels https://conda.binstar.org/rsignell

conda config --add channels https://conda.binstar.org/Unidata

conda create -n workshop python=2 numpy matplotlib cartopy ipython ipython-notebook \
    netcdf4 owslib pyudl networkx basemap

```
