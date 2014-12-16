
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

###Wakari
1. Constructed from an email exchange with Rich Signell   
    2.  Rich Signell made us an account for Wakari Enterprise on a machine and pointed us to information for creating the custom environment needed for running system test or other IOOS stuff at [http://goo.gl/vsZn7x](http://goo.gl/vsZn7x).
    2.  I found that the instructions as written did not let me complete the install step at `conda install iris, pyoos netcdf4`, complaining about permissions on the `/opt/wakari/anaconda` directory. 
        3.  One way to get past that is to specify the path to the environment with the -p option, so: `conda install -p /projects/rsignell/test/envs/my_root iris, pyoos netcdf4`. 
        4.  A more sensible alternative is to create and activate the environment first then do the install step, and the packages get installed into the local environment instead of into the master environment, which is what would have happened if I had been using a user install of anaconda. 
    2. I then had a further confusing experience with Wakari on the testbed machine: I had a project working over the weekend, it was compiling and running its notebook and doing some things. I shut it down, pushed my commits to github, and went away and came back to do some more things with it, and it had stopped working. The message was "Warning, notebook server is running IPython version, 2.0.0-dev, The kernel (directory of project)/bin/python is running a different version."  I started from scratch and reinstalled and recreated everything. 
    2. Then it did it again. I shut down the project I was working on, left it alone overnight and came back in the morning to start it up again and got the same message. Current status: Continuum support is working on the problem.    
1.  I now have an AWS VM available and moved operations over there.
    2.  Following the same kind of environment creation steps as Rich outlined, I got the IPython notebook working. But here it would not read or recognise any netCDF file. 
    2.  Backing out, I went back to the Unidata python workshop examples and worked with their test-data. Behold! Some of them worked (were able to be read), but files fetched from one of the THREDDS servers pointed to by IOOS were broken and not recognised as netCDF. Went back to the original workshop environment and, again, Behold! It works. So something in the environment created with Rich's steps is messing with the system or missing. So far ...   
1.  An email from Jeremy Langley, support at Continuum, provides a lot of enlightenment: 

    > This error is caused by upgrading Ipython.  We need to know how ipython was upgraded in order to help you better.
    >
    > If you ran the lines from this page:
    > [http://rsignell.tiddlyspot.com/#[[Creating%20a%20custom%20Conda%20environment%20on%20Wakari%20Enterprise]]]
    > 
    > There is a line:    
    > `conda config --add channels https://conda.binstar.org/rsignell`    
    > It points to another install of ipython that doesn't work with your version of Wakari.  (despite the version numbers, which caused considerable debate here.)
    > 
    > The way to install wakari to an environment is running:    
    > `conda install -c wakari ipython-we=2.0.0.1`    
    > 

###Local IPython

    After working a while on a notebook, I began to have trouble with
`matplotlib` not loading properly, and being unable to find all required
modules, resulting in plots not displaying. 

    The resolution was to re-install anaconda and re-create the  environments. 

    Recommendation: 
    - keep track of the packages installed, by doing   
```
	conda list -e -n [env-name] 
```

    and piping the output into a `requirements.txt` file. This will allow you
to quickly get the environment set up again after you have nuked and
re-installed Anaconda.

    Tracking down the cause of the breakdown, it may be
that when I needed another package to be imported and it was not available in
the base Anaconda install, I did `conda install` in the working environment,
instead of in the default anaconda environment. It may be that then the working
environment and default environment got out of sync and 
package dependencies were broken. 

    Try removing the environment entirely (`conda remove -n [enviname] --all`) and then recreating it (`conda create -n [envname] -f requirements.txt`). 

##Trouble-shooting

Have you run into an unexpected difficulty for no apparent reason? Routes for resolution include:

1. Ask a question of google.    
    I have found that typing the question I have, e.g., "How do I find process ID of running ipython notebook?", 
produces better and quicker results than trying to guess at possible terms.
Often asking Google the question turns up the exact question with the answer on
Stack Exchange or the Ubuntu Forums.
2. When you get tired of flailing around on Google, post a question to 
one of the Stack Exchange forums
([Stackoverflow](http://stackoverflow.com/questions/tagged/python) seems to get most of the 
python questions) and wait for an answer.
3. When you get an answer add the incident and resolution here, or in the section above: it may help someone.




<!-- vim: se nowrap tw=0 : -->

