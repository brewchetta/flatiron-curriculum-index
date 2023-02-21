# Environment Setup

## Learning Goals

    - Use pyenv to use different Python versions
    - Set up virtual environment using pipenv

## Key Vocab

    - Module: a file containing Python definitions and statements. A module's functions, classes, and global variables can be accessed by other modules.
    - Package: a collection of modules that can be accessed as a group using the package name.
    - import: the Python keyword used to access data from other packages and modules inside of the current module.
    - PyPI: the Python Package Index. A repository of Python packages that can be downloaded and made available to your application.
    - pip: the command line tool used to download packages from PyPI. pip is installed on your computer automatically when you download Python.
    - Virtual Environment: a collection of modules, packages, and scripts that can be activated or deactivated at any time.
    - Pipenv: a virtual environment tool that uses pip to manage the modules, packages, and scripts that you intend to use in your application.

## Introduction

In this lesson we will talk about environment tools like pyenv and pipenv. These tools allows us to separate different Python environments for all kinds of use cases. This is useful when we need an isolated environment with libraries and specific versions of Python.
Pyenv

Run the following command to see if pyenv has installed.

```bash
$ pyenv versions
* system (set by /Users/username/.pyenv/version)
```

We can see the different versions of Python available to install using the following command

```bash
$ pyenv install -l
Available versions:
  2.1.3
  2.2.3
  2.3.7
  ...
  ...
```

Lets install a new version of Python (3.9.2). We can do this using the following command

`pyenv install 3.9.2`

To set the global Python version to the one we have installed

`pyenv global 3.9.2`

Now we can run Python code with the version of Python we want to use.
Pipenv

Pyenv allows us to manage the version of Python we are working with.

What if we want to manage dependencies as well?

Pipenv automatically creates and manages a virtualenv for your projects, it also adds/removes packages from your Pipfile as you install/uninstall packages

To create a virtual environment using pipenv we can use the following command.

`pipenv --python 3.8.13`

In the Python flag we can define which version of `--python` we want to use.

You will notice a Pipfile and a Pipfile.lock have been added to the directory.

The Pipfile describes the dependencies we have installed and the Python version.

The Pipfile.lock describes all the dependencies our dependencies rely on. The lock file gives us the ability to produce a deterministic and reproducible project environment.

We can now install a library into the virtual environment. Lets use the requests library as an example

`pipenv install requests`

if we want to install a specific version of the requests library we can pin the version in the command

`pipenv install requests==2.28.1`

Pipenv has created a virtual environment for our project. We can see the location of this virtual environment by using the command

```bash
$ pipenv --venv
/Users/username/.local/share/virtualenvs/python-p3-environment-setup-6aKrLSzT
```

Pipenv allows us to install dev dependencies. We can do so by adding the --dev argument.

`pipenv install pytest --dev`

Pytest will be added to the Pipfile as a dev dependency

Dev dependencies are modules which are not needed in production but they help us develop and test the code.

How do we get into our virtual environment?

Using the following command we can use the virtual environment and run commands inside of it.

`pipenv shell`

Now we are in the virtual environment and have access to the dependencies we defined in the Pipfile. If we run the following commands in the virtual environment we will see that we can import the requests module we installed using pipenv install requests.

```bash
python
>>> import requests
>>>
```

If you ever need to remove a virtual environment you can use the pipenv --rm command. This command can help you debug any conflicting environment issues. After running the remove command you can run pipenv install again to create a new virtual environment.

Now we can write all our code in this directory and run it in the deterministic virtual environment. If we have a Python file called program.py we can use the following command to run it in the virtual environment.

`pipenv run python program.py`

## Conclusion

Virtual environments allow us to have a deterministic and predictable runtime for our Python projects. We can define specific versions for Python and the dependencies we need. We can easily add new virtual environments for multiple projects we have on our machine.
