# PyPi and Pip

## Learning Goals

- Installing packages using pip.

***

## Key Vocab

- **Module**: a file containing Python definitions and statements. A module's
functions, classes, and global variables can be accessed by other modules.
- **Package**: a collection of modules that can be accessed as a group using
the package name.
- **`import`**: the Python keyword used to access data from other packages and
modules inside of the current module.
- **PyPI**: the **Py**thon **P**ackage **I**ndex. A repository of Python
packages that can be downloaded and made available to your application.
- **`pip`**: the command line tool used to download packages from PyPI. `pip`
is installed on your computer automatically when you download Python.
- **Virtual Environment**: a collection of modules, packages, and scripts that
can be activated or deactivated at any time.
- **Pipenv**: a virtual environment tool that uses `pip` to manage the modules,
packages, and scripts that you intend to use in your application.

***

## Introduction

Package Installer for Python (Pip) is the default package manager for python
and is used to install and manage software packages. It uses an online
repository called Python Package Index (PyPi).

We can search PyPi for libraries using the search bar on the site.

![Example image for uploader](https://curriculum-content.s3.amazonaws.com/pypiscreenshot.png)

## Installing Packages using Pip

We can use the Pip command to install python packages from the Python Package Index (PyPi).
Lets practice this using a package called `requests`.
Requests is a HTTP library for the Python programming language.

```bash
pip install requests
```

Now we have access to the requests module. It can be imported in our python programs.

```bash
$ python
>>> import requests
```

To install a specific version of the module we can use `pip` install

```bash
pip install requests==2.22.0
```

Requirements files are files containing a list of modules to be installed using `pip` install.

```bash
pip install -r requirements.txt
```

Constraints files are requirements files that only control which version of a requirement is installed, not whether it is installed or not.

```bash
pip install -c constraints.txt
```

Example of a requirements.txt or constraints.txt file.

```bash
requests==2.28.1
uvicorn==0.18.2
fastapi==0.79.0
```

To uninstall a package

```bash
pip uninstall requests
```

## Conclusion

Pip can be used to install packages from the Python Package Index. It gives us access
to many libraries to help us develop.
***

## Resources

- [Python 3 Documentation](https://docs.python.org/3/)
- [pip](https://pip.pypa.io/en/stable/user_guide/)
- [PyPi](https://pypi.org/)
