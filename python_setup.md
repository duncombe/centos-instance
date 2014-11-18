
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

`conda install -f requirements.txt`


Tried this
```
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
```

It was a while ago ...   
and I cannot remember whether it was this that worked or not, but now in the appropriate compliance checker directory on the VM, the following commands do work (i.e., generate output):

``` 
source activate compliance-checker
compliance-checker --test=acdd  compliance_checker/tests/data/ru07-20130824T170228_rt0.nc
```

so clearly something was done to get the correct response. A test should be done to see if the result can be replicated with a newly created anaconda install and freshly cloned repository. 


##More about python and IPython 

1. Constructed from an email exchange with Rich Signell   
    2.  Rich Signell made us an account for Wakari Enterprise on a machine and pointed us to information for creating the custom environment needed for running system test or other IOOS stuff at [http://goo.gl/vsZn7x](http://goo.gl/vsZn7x).
    2.  I found that as the instructions were written the system would not let me complete the install step at `conda install iris, pyoos netcdf4`, complaining about permissions on the `/opt/wakari/anaconda` directory. To get past that I had to specify the path to the environment with the -p option, so: `conda install -p /projects/rsignell/test/envs/my_root iris, pyoos netcdf4`. An alternate is to create and activate the environment first then do the install step, and the 
    2. I then had a further confusing experience with Wakari on the testbed machine: I had a project working over the weekend, it was compiling and running its notebook and doing some things. I shut it down, pushed my commits to github, and went away and came back to do some more things with it, and it had stopped working. The message was "Warning, notebook server is running IPython version, 2.0.0-dev, The kernel (directory of project)/bin/python is running a different version."  I started from scratch and reinstalled and recreated everything. 
    2. Then it did it again. I shut down the project I was working on, left it alone overnight and came back in the morning to start it up again and got the same message. Current status: Continuum support is working on the problem.    
1.  I now have an AWS VM available and moved operations over there.
    2.  Following the same kind of environment creation steps as Rich outlined, I got the IPython notebook working. But here it would not read or recognise any netCDF file. 
    2.  Backing out, I went back to the Unidata python workshop examples and worked with their test-data. Behold! Some of them worked (were able to be read), but files fetched from the THREDDS server at IOOS were broken and not recognised as netCDF. Went back to the original workshop environment and, again, Behold! It works. So something in the environment created with Rich's steps is messing with the system or missing. So far ...   
1.  Further updates as events warrant.



