# Python Package Installer

So far we've used only built-in modules and our own modules. 
* However, the Python community members often create packages aswell and make their code accessible to any Python developer. 
*  We can find them in a centralized repository called **PypI**, that contains all available software packages, which is maintained by a workgroup called Packaging Working Group.
    * PyPI stands for Python Package Index
* This repo is completely free and we're allowed to use any code from it. 
* We can access this repo with a tool called **PIP**.

## PIP

With PIP, we can install packages that are available in the PyPI repo. Before, we can use PIP, we might have to install it because some Python installations come with PIP and some don't. 
* You can check if you have PIP installed by typing the following command in the terminal
```
pip --version
```
* It returns the version of PIP installed on your computer.

PIP uses the internet to query PyPI and download the required packages. 
* So you need an working network connection to work with PIP.

You can browse through different packages in the PyPI website &rarr; https://pypi.org/. If you found a package that you'd like to use in your project, you can install it with the following command
```
pip install [package_name]
```
---
After it's been installed, you can see some extra information about the package with the following command
```
pip show [package_name]
```
* This command tells you who made it, what version of it is installed, a description and possible dependencies.
    * Dependencies are other modules that the installed package needs in order to run.
---
If you need to list all the packages available locally, you can do so by using the following command
```
pip list
```
---
If you no longer need a package, you can uninstall it with the following command
```
pip uninstall [package_name]
```

