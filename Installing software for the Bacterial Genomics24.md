
-------------------------------------------------------------
**Conda**
========
To install conda, run the following script

`wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh`

Once the download is complete, run this script:

`bash Anaconda3-2023.09-0-Linux-x86_64.sh`

The first time you call conda you might get the error below:

_conda: command not found_

If that happens, run this script to add conda to path:

`export PATH=~/anaconda3/bin:$PATH`

But again, if you refresh the shell, you will bump into conda: command not found again. So, add the script to the bashrc file.

Open bashrc using 

`nano ~/.bashrc`

Then add the `export PATH=~/anaconda3/bin:$PATH` at the bottom of the file. Click **ctrl + o**, to save, press enter, then **ctrl + x** to exit. 

**Configuring bioconda**

**Run the following scripts to configure Bioconda**
```
conda config --add channels defaults
conda config --add channels biocondac
conda config --add channels conda-forge
```
