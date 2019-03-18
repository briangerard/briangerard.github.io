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

### Before You Start

If you use bash, you will want to add the following to your `~/.bashrc` file:

```bash
VENVWRAPPER_LIB=$(type -P virtualenvwrapper.sh)
if [[ (-n $VENVWRAPPER_LIB) && (-r $VENVWRAPPER_LIB) ]]
then
    . $VENVWRAPPER_LIB
fi
```

Once that's been added, you can re-read it into your current shell by running:

```bash
bash$ . ~/.bashrc
```

Or by just restarting the shell:

```bash
bash$ exec bash
```

Once that's been done, the rest of the commands mentioned below become available.

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

Note that this will also activate the 'my-project' virtual environment.  So, after you've
run that command, you are *in* the 'my-project' virtual environment.  See the
'Deactivation' section below if you want to get back out of it.

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

### Bonus: Showing the Current Virtual Environment

There's no built-in function for telling you if you're currently in a virtual environment,
and if so, which one.  Luckily, this is easy enough to hack around.

If you use bash, add this to the end of your `~/.bashrc` file:

```bash
alias currentvirtualenv='if [[ -n $VIRTUAL_ENV ]]; then basename $VIRTUAL_ENV; else echo
"Not in a virtualenv"; fi'
```

That will provide a `currenvirtualenv` command whenever you log in from then on.

In order to get it in the same shell where you edited the `.bashrc`, you can just source
the file:

```bash
bash$ . ~/.bashrc
```

After that, you can use it from the command line:

```bash
bash$ currentvirtualenv
my-project
bash$ deactivate
bash$ currentvirtualenv
Not in a virtualenv
```

### Further Reading

There are a number of resources for learning to use virtual environments.  This list is
meant to give you a couple of starting points.

These are some other overview-type pages that go into more depth than the "quick start"
approach we took here:
* [https://codeburst.io/understanding-python-installation-and-virtualenv-a-friendly-guide-for-beginners-and-2b82859b06ae](Overview)
  from Deepak Aggarwal at [https://codeburst.io](codeburst.io)
* [https://www.bogotobogo.com/python/python_virtualenv_virtualenvwrapper.php](Another one)
  from the folks at [https://www.bogotobogo.com/index.php](bogotobogo.com)
* And then there's the [https://virtualenvwrapper.readthedocs.io/en/latest/](official virtualenvwrapper docs),
  from [https://readthedocs.org/](readthedocs.org)

