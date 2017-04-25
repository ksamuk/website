+++
date = "2016-04-20T12:00:00"
draft = false
tags = ["academic", "popgen"]
title = "Getting Started with dadi for Windows Users"
math = true
summary = """
A guided on installation of the population genetics Python package dadi
"""

[header]
image = "headers/dadi_pic.png"
caption = "Image credit: [**Gutenkunst et al. 2009**](http://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1000695)"

+++

$\partial$a$\partial$i is a powerful and flexible population genetics model-fitting package for Python 2.X written by [Ryan Gutenkunst](http://gutengroup.mcb.arizona.edu/). It is fairly popular in the population and evolutionary genetics literature for evaluating the fit of demographic models to DNA polymorphism data.

$\partial$a$\partial$i is slightly unusual that it is a Python package rather than a standalone piece of software. This makes using $\partial$a$\partial$i very interactive, particularly if one uses a dynamic coding platform such a Jupyter notebook. 

It also has optional, but extremely handy functions that allow you to call the program *ms* by Richard Hudson directly Python in order to simulate data. So *ms* and a working Python 2.7 (32 bit) installation are both prerequisites, which in turn have other prerequisites.

I normally use Mac OS and/or a Linux computing cluster for all my scientific computing. However, I recently installed dadi and all its dependencies from scratch on my Windows 10 PC. It was bit of a saga, and I wanted to share the exact steps I took, so as to ease the process for others.

Things that need to be installed (if you don't have them already):

- Anaconda 2.7 (32 Bit version)
- Cygwin
- The gcc compiler
- ms
- dadi 

## Install Anaconda 2.7 (32 bit)

Anaconda is a pre-packaged version of Python maintained by Continuum Analytics. It includes a number of useful scientific packages, utilities, and a package manager in a single installation.

1. Uninstall any previous versions of Anaconda + restart Windows.

2. Install using the **32 bit** Anaconda installer available [here](https://www.continuum.io/downloads).

3. Restart windows.

## Install Cygwin + gcc compiler

ms requires compilation from source. If you do not have a compiler installed, installing Cygwin will allow you to quickly install the gcc compiler. Cygwin also gives access to many Linux-like utilities.


1. To install Cygwin, Follow Steps 1 & 2 [here](http://preshing.com/20141108/how-to-install-the-latest-gcc-on-windows/). 

2. After installing Cygwin, move the setup-x86_64.exe file you used to install Cygwin to the folder where you chose install Cygwin. Navigate to that folder in a command prompt. To install gcc, type:

		setup-x86_64.exe -q -P wget -P gcc-g++ -P make -P diffutils -P libmpfr-devel -P libgmp-devel -P libmpc-devel

3. Add the cygwin64/bin folder to your [system path](http://www.zdnet.com/article/windows-10-tip-point-and-click-to-edit-the-system-path-variable/).

## Install Richard Hudson's *ms*

1. Download and extract the zipped version of *ms* from the [ms website](https://uchicago.app.box.com/s/l3e5uf13tikfjm7e1il1eujitlsjdx13). 

2. Navigate to the folder where you extracted *ms*, and run:

		gcc -o ms ms.c streec.c rand1.c -lm

3. Add the folder containing ms.exe (the *ms* folder) to your [system path](http://www.zdnet.com/article/windows-10-tip-point-and-click-to-edit-the-system-path-variable/).

## Install the latest version of $\partial$a$\partial$i

1. Go here: https://bitbucket.org/gutenkunstlab/dadi/downloads/ and choose "download repository" (not the .exe). 

2. Extract the contents to a folder (anywhere).

3. Navigate to the extraction folder in a command prompt. Then type:

		python setup.py install
		
Scan the output of this command for errors. Depending on the state of your system, you may need to install Visual Studio 9.0 C++ (follow the url given in error message).
		
## Run the $\partial$a$\partial$i example analysis

To confirm your installation works, run the example analysis provided in the repository you downloaded.

1. Copy the "example/YRI_CEU" folder from the extracted repository to a new folder (anywhere).

2. Open the Jupyter application.

3. In the file browser tab Jupyter opens, navigate to the newly created YRI_CEU folder and Create a new Python 2 notebook. This will open a new tab with a Python 2 notebook.

4. Open the 'YRI_CEU.py' script from the Jupyter file browser. This will open the script in a separate browser tab.

5. Copy,  paste and run (logically-selected) chunks of code from the .py to your new Python 2 notebook. 

6. Check for error messages + troubleshoot if necessary.


## Finished!

If the gods have smiled on you, you should now how a functioning installation of dadi. Before diving into an analysis, I highly recommend the following references by Ryan Gutenkunst et al.:

## Reading list

1. [The original paper describing dadi](http://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1000695)

2. The dadi manual.

3. [A paper describing the use of the Godambe Information Matrix for model comparison in dadi](https://academic.oup.com/mbe/article-lookup/doi/10.1093/molbev/msv255)

4. [A recent paper about integrating two-locus statistics into dadi](http://www.genetics.org/content/early/2017/04/13/genetics.117.201251)

