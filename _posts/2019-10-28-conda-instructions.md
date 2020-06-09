---
layout: post
title: Conda Quicknotes
excerpt: <i>About massive environment managers</i>
---

This is a short post with a few Conda commands and notes. I am adding my most frequently using commands. Use carefully, YMMV. I am sourcing 
these from the Conda Docs<a href='#references'><sup>1</sup></a>. It is mainly intended as a quick reference for myself.

## Basics and Introduction:
Conda is a package and environment manager primarily for Python. For our current context, it helps in installing packages while 
resolving their dependencies. Conda also helps in creating environments which I think of as isolated boxes with their own set of 
versions of packages (and even python). 

We can switch across environments without worrying if installing a new package will create conflicts. For eg, a new package C might 
need version x.x of package B while an already existing package A needs version x.y. Without environments, this could lead to 
dependency issues.

This environment information is also useful when we share our issues/packages etc where we can specify exactly which version of each 
package is required to either reproduce our problem or to install and work properly on our package. 

Conda requires an Anaconda (or Miniconda) installation. Once it is installed on Windows, all the conda commands are accessible from the 
Anaconda Prompt which can be invoked from the Start Menu. 

To verify that conda is available, check:

```
conda --version
```

To update to lastest version of conda:

```
conda update conda
```

## Most used commands
To create a new environment:

```
conda create --name myenv
```

This creates an environment with the same python version as the Anaconda installation. To create an environment with a different version
of python (say 3.5):

```
conda create --name myenv python=3.5
```

These create environments with a default set of packages. 
To create an environment of python 3.5 and installing a particular package of required version:

```
conda create --name myenv package_name=version python=3.5
```

It is recommended to install all the packages required in an environment in one go. 
To activate the created environment:

```
conda activate myenv
```

To go back to base environment:

```
conda activate
```

To install a package using conda:

1. Search for the package

    ```
    conda search package_name
    ```

2. Install the package

    ```
    conda install package_name
    ```

3. Verify it is installed

    ```
    conda list
    ```

We can also use pip along with conda. To use pip in the environment, first install pip:

```
conda install -n myenv pip
```

Conda and pip can have conflicts. So install as much as possible using conda. Other recommendations can be seen from [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#using-pip-in-an-environment)

To remove an environment:

```
conda remove --name myenv --all
```

These are the basic commands that I think should be most useful. If I find more commands, I will update this post. 

'Til Later
<footer id="references"></footer>
References:
1. [Conda Docs](https://docs.conda.io/en/latest/)
2. [Tim Hopper's Blog](https://tdhopper.com/blog/my-python-environment-workflow-with-conda/)
