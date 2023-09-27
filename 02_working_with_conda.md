# Working with Conda environments

Most of the times, when working on shared workstations or servers, you are not given administrative permissions. That is, you are not allowed to freely roam around and manage directories or install softwares. This is basically for your (and everyone's) safety, so that for example important files are not damaged by mistake. Though, you will need for sure to install new softwares for your analyses. So how can you be able to get programmes without asking every time your administrator? Conda comes into help!!

## Table of contents
   - [Conda is a package and environment management system](#conda-is-a-package-and-environment-management-system)
   - [<code>conda create</code> to create a new Conda environment](#conda-create-to-create-a-new-environment)
   - [<code>conda install</code> to install a software](#conda-install-to-install-a-software)
   - [<code>conda env list</code> to list all Conda environments](#conda-env-list-to-list-all-conda-environments) 🚧
   - [Export a Conda environment to a YAML file](#export-a-conda-environment-to-a-yaml-file) 🚧
   - [Remove a Conda environment](#remove-a-conda-environment) 🚧

## Command cheat sheet
| Command | Description |
| --- | --- |
| [<code>conda create</code>](#conda-create-to-create-a-new-conda-environment) | Create a new Conda environment |
| [<code>conda activate</code>](#conda-install-to-install-a-software) | Activate a Conda environment |
| [<code>conda deactivate</code>](#conda-install-to-install-a-software) | Deactivate a Conda environment |
| [<code>conda install</code>](#conda-install-to-install-a-software) | Install a software and required dependencies by mean of Conda |

## Conda is a package and environment management system
**[Conda](https://docs.conda.io/en/latest/)** is a software that helps you install other softwares by also taking care of managing all the requeried dependencies.

Besides helping in installing without administrative privileges, Conda is also really useful to resolve conflicts between programming language and package versions. So, for example, if you need two softwares, one requiring python v2.7 and one requiring python v3.1, with Conda you can install both of them with litte or no effort.

Conda accomplishes this by **operating within environments**. You can think of a Conda environment as... a natural environment. Like the Amazon, the Sahara and the Mediterranean evironments—which are section of the natural world with their own species assemblage, temperature and rain conditions—each Conda environments are sections (directories) of your computer with their own packages and versions of programming languages. The only difference with natural environments is that Conda environments are independent one to the others and do not exchange information (or data).

<p align="center">
<img src="https://github.com/filonico/UNIX_and_bash_basics/assets/72141380/20bebc36-5717-47c3-97b8-b2c53ed1ab75" height="100">
</p>

[↑ Table of contents ↑](#table-of-contents)

## <code>conda create</code> to create a new Conda environment

To start working with Conda and get a new software installed, you first need to **create the environment** in which the software will be hosted:

```bash
# create a new Conda environment
$ conda create -n my_env_name
```

The newly created environment is now empty and just waits to be filled up with installations.

If you have a configuration file ([YAML file](https://en.wikipedia.org/wiki/YAML), which is indicated by the <code>.yml</code> extension) of another Conda environment, you can type:

```bash
# create a new Conda environment
$ conda env create -f environment.yml
```
This is the easiest way to clone already-existing Conda environments: you just need the relative YAML file (see here to know how to get a YAML file from a Conda environment).

[↑ Table of contents ↑](#table-of-contents)

## <code>conda install</code> to install a software

Before installing a software into a Conda environment, make sure the environment is active:

```bash
# activate a new Conda environment
$ conda activate my_env_name
```
Once the environment has been activated, the terminal will display its name in brackets before the prompt symbol.

To install a new software, just check in the [Anaconda website](https://anaconda.org/) (the repository where tons of data science packages are provided) if the package is available as a Conda distribution (very advanced tip: just google your software name followed by "conda" ;-) ). Then follow the instruction on the website.

```bash
# to install IQTREE2 with Conda, first of all let's create an environment and activate it
$ conda create -n iqtree_env
...
$ conda activate iqtree_env
...
# then just follow the instructions on the Anaconda website. So let's type the following. Note that the name of the activate Conda environment is displayed before the '$'
(iqtree_env) $ conda install -c bioconda iqtree
...
```
If you want to quit the working Conda environment, just type:
```bash
# activate a Conda environment
$ conda deactivate
```

[↑ Table of contents ↑](#table-of-contents)

## <code>conda env list</code> to list all Conda environments

**🚧🚧 WORK IN PROGRESS 🚧🚧**

[↑ Table of contents ↑](#table-of-contents)

## Export a Conda environment to a YAML file

**🚧🚧 WORK IN PROGRESS 🚧🚧**

[↑ Table of contents ↑](#table-of-contents)

## Remove a Conda environment

**🚧🚧 WORK IN PROGRESS 🚧🚧**

[↑ Table of contents ↑](#table-of-contents)