# Getting Started With Virtualenvs

## What's A Virtual Environment?

A virtual environment is a way to have an "enclosed" environment in which to do Python
development without affecting the system as a whole, or other virtual environments.  In
practical terms, that means that a virtual environment has its own python executable and
modules installed.  When you're using a virtual environment, you can use 'pip' (or 'pip3')
to install a Python library without having to be root to do so.

## How To Set It Up

Installing virtualenv is relatively simple.

For Debian-based systems:

```bash
bash$ sudo apt install virtualenv
```

Or, using pip:

```bash
bash$ sudo pip install virtualenv
```

That's technically all you need, but there's one more thing I would recommend you install.
The [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) package
provides some convenient aliases for working with and managing virtual environments.  It's
not strictly necessary, but it does make virtual environments more convenient.

To install that, you use pip:

```bash
bash$ pip install virtualenvwrapper
```

## Basic Usage

The most basic tasks needed to use virtual environments are creation, activation, and
deactivation.  Obviously, you can do more, but this is the essential start.

### Creation

First, while it's not required that each virtual environment have its own directory, I
would recommend it.  By that I mean the directory which contains all of your own code that
you develop in the virtual environment.  Keeping each separate ensures that no project's
prerequisites can interfere with any other's, for example.

So, to create a virtual environment called "my-project", which will use python 3:

```bash
bash$ cd
bash$ mkdir my-project
bash$ mkvirtualenv -a $HOME/my-project -p $(which python3) my-project
```

### Activation

In order to start working in a pre-existing virtual environment, you just need to use the
'workon' function.

To activate the virtual environment we previously created:

```bash
bash$ workon my-project
```

If you don't recall the names of all of your virtual environments offhand, you can list
them all using 'lsvirtualenv' function:

```bash
bash$ lsvirtualenv -b
my-project
some-other-project
yet-another-project
```

### Deactivation

Eventually, you'll probably need to **stop** working in a virtual environment.  To do
that, you just need to use the 'deactivate' function:

```bash
bash$ deactivate
```

If you try to run 'deactivate' when you're **not** in a virtual environment, it won't be
defined:

```bash
bash$ deactivate
bash: deactivate: command not found
```
