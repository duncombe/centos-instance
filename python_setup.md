
# Setting up a python environment

Taken from Unidata Python workshop, to be modified for compliance checker, system-test.

```
git clone https://github.com/Unidata/unidata-python-workshop

conda config --add channels https://conda.binstar.org/rsignell

conda config --add channels https://conda.binstar.org/Unidata

conda create -n workshop python=2 numpy matplotlib cartopy ipython ipython-notebook \
    netcdf4 owslib pyudl networkx basemap

```

For compliance checker:

conda install -f requirements.txt


Tried this
curl -sL https://raw.githubusercontent.com/brainsik/virtualenv-burrito/master/virtualenv-burrito.sh | $SHELL
source /home/cduncomberae/.venvburrito/startup.sh
mkvirtualenv --no-site-packages compliance-checker
pip install numpy
conda install pip
pip install numpy
pip install compliance-checker
compliance-checker --test=acdd test-data/ru07-20130824T170228_rt0.nc
compliance-checker --test=acdd compliance_checker/tests/data/sss20140107.v2.0cap.
git clone ssh://git@github.com/duncombe/compliance-checker.git

