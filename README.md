Machine Learning Notebooks with Java
==========================

This project aims at teaching you the fundamentals of Machine Learning in
java. Mission is to rewrite al the example code and solutions to the exercises in the O'Reilly book [Hands-on Machine Learning with Scikit-Learn and TensorFlow](http://shop.oreilly.com/product/0636920052289.do) in Java instead of python in the main project:


# Installation

First, you will need to install [git](https://git-scm.com/), if you don't have it already.

Next, clone this repository by opening a terminal and typing the following commands:

    $ cd $HOME  # or any other development directory you prefer
    $ git clone https://github.com/ageron/handson-ml.git
    $ cd handson-ml

If you do not want to install git, you can instead download [master.zip](https://github.com/ageron/handson-ml/archive/master.zip), unzip it, rename the resulting directory to `handson-ml` and move it to your development directory.

If you want to go through chapter 16 on Reinforcement Learning, you will need to [install OpenAI gym](https://gym.openai.com/docs) and its dependencies for Atari simulations.

If you are familiar with Python and you know how to install Python libraries, go ahead and install the libraries listed in `requirements.txt` and jump to the [Starting Jupyter](#starting-jupyter) section. If you need detailed instructions, please read on.

## Python & Required Libraries
Of course, you obviously need Python. Python 2 is already preinstalled on most systems nowadays, and sometimes even Python 3. You can check which version(s) you have by typing the following commands:

    $ python --version   # for Python 2
    $ python3 --version  # for Python 3

Any Python 3 version should be fine, preferably 3.5 or 3.6 (TensorFlow support for Python 3.7 is [coming soon](https://github.com/tensorflow/tensorflow/issues/20517)). If you don't have Python 3, I recommend installing it (Python ≥2.6 should work, but it is deprecated so Python 3 is preferable). To do so, you have several options: on Windows or MacOSX, you can just download it from [python.org](https://www.python.org/downloads/). On MacOSX, you can alternatively use [MacPorts](https://www.macports.org/) or [Homebrew](https://brew.sh/). If you are using Python 3.6 on MacOSX, you need to run the following command to install the `certifi` package of certificates because Python 3.6 on MacOSX has no certificates to validate SSL connections (see this [StackOverflow question](https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error)):

    $ /Applications/Python\ 3.6/Install\ Certificates.command

On Linux, unless you know what you are doing, you should use your system's packaging system. For example, on Debian or Ubuntu, type:

    $ sudo apt-get update
    $ sudo apt-get install python3

Another option is to download and install [Anaconda](https://www.continuum.io/downloads). This is a package that includes both Python and many scientific libraries. You should prefer the Python 3 version.

If you choose to use Anaconda, read the next section, or else jump to the [Using pip](#using-pip) section.

## Using Anaconda
When using Anaconda, you can optionally create an isolated Python environment dedicated to this project. This is recommended as it makes it possible to have a different environment for each project (e.g. one for this project), with potentially different libraries and library versions:

    $ conda create -n javaml python=3.5 anaconda
    $ conda activate javaml

This creates a fresh Python 3.5 environment called `javaml` (you can change the name if you want to), and it activates it. This environment contains all the scientific libraries that come with Anaconda. This includes all the libraries we will need (NumPy, Matplotlib, Pandas, Jupyter and a few others), except for TensorFlow, so let's install it:

    $ conda install -n javaml -c conda-forge tensorflow

This installs the latest version of TensorFlow available for Anaconda (which is usually *not* the latest TensorFlow version) in the `javaml` environment (fetching it from the `conda-forge` repository). If you chose not to create an `javaml` environment, then just remove the `-n javaml` option.

Next, you can optionally install Jupyter extensions. These are useful to have nice tables of contents in the notebooks, but they are not required.

    $ conda install -n javaml -c conda-forge jupyter_contrib_nbextensions

You are all set! Next, jump to the [Starting Jupyter](#starting-jupyter) section.



### Requirements for  Java Kernel

1.  [Java JDK >= 9](http://www.oracle.com/technetwork/java/javase/downloads/index.html). **Not the JRE**. Java 11 is the current release and should be considered if selecting a version but if a java 9 or 10 build is installed, everything _should_ still be working fine.

    1.  Ensure that the `java` command is in the PATH and is using version 9. For example:
        ```bash
        > java -version
        java version "9"
        Java(TM) SE Runtime Environment (build 9+181)
        Java HotSpot(TM) 64-Bit Server VM (build 9+181, mixed mode)
        ```

    2.  Next ensure that `java` is in a location where the jdk was installed and not just the jre. Use the `java --list-modules` command to do this. The list should contain `jdk.jshell`.

        *   On *nix `java --list-modules | grep "jdk.jshell"`
        *   On windows `java --list-modules | findstr "jdk.jshell"`

        Both should output `jdk.jshell@` followed by your java version.

    If the kernel cannot start with an error along the lines of
    ```text
    Exception in thread "main" java.lang.NoClassDefFoundError: jdk/jshell/JShellException
            ...
    Caused by: java.lang.ClassNotFoundException: jdk.jshell.JShellException
            ...
    ```
    then double check that `java` is referring to the command for the `jdk` and not the `jre`.
    
2.  Some jupyter-like environment to use the kernel in.

    A non-exhaustive list of options:

    *   [Jupyter](http://jupyter.org/install)
    *   [JupyterLab](http://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html)
    *   [nteract](https://nteract.io/desktop)
### Installing   Java Kernel
The Java Kernel is from (https://github.com/SpencerPark/IJava)

1.  Run the commands below

    ```bash
    # Pass the -h option to see the help page
    > python3 install.py -h

    # Otherwise a common install command is
    > python3 install.py --sys-prefix
    ```

2.  Check that it installed with `jupyter kernelspec list` which should contain `java`.



## Starting Jupyter
If you want to use the Jupyter extensions (optional, they are mainly useful to have nice tables of contents), you first need to install them:

    $ jupyter contrib nbextension install --user

Then you can activate an extension, such as the Table of Contents (2) extension:

    $ jupyter nbextension enable toc2/main

Okay! You can now start Jupyter, simply type:

    $ jupyter notebook --kernel=java

This should open up your browser, and you should see Jupyter's tree view, with the contents of the current directory. If your browser does not open automatically, visit [localhost:8888](http://localhost:8888/tree). Click on `index.ipynb` to get started!

Note: you can also visit [http://localhost:8888/nbextensions](http://localhost:8888/nbextensions) to activate and configure Jupyter extensions.

Congrats! You are ready to learn Machine Learning, hands on!


