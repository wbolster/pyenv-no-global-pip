pyenv no-global-pip
===================

This is an addition for [pyenv](https://github.com/pyenv/pyenv) to prevent accidental `pip` commands outside a virtual environment (`venv`/`virtualenv`).

Why?
----

`pyenv` makes it easy to have many different Python versions installed, and select the one to use for a specific project.

While `pyenv` manages Python installation elegantly, different Python versions provide their own `pip` versions, and depending on how you install and use `pyenv`, there will be many `pip` and `pipX.Y` binaries in your `$PATH`, each of them pointing to a different Python installation.

It is easy to accidentally run those `pip` commands outside a virtual environment, polluting global Python installations by installing libraries and binaries that should not be installed globally.

To install ‘global’ Python tools outside a project's virtual environment, consider using a tool like [pipx](https://github.com/pipxproject/pipx) to isolate all tools (and its dependencies) into automatically managed virtual environments.

How?
----

This repository can be used as a ‘fake’ installed Python version for use with `pyenv`. It provides a bunch of `pip`, `pipX`, and `pipX.Y` commands that will simply trigger an error when invoked. The result is that it is impossible to accidentally run `pip` outside a virtual environment, and mess up your Python installations.

Clone this repo into `~/.pyenv/versions/no-global-pip`:

```
cd ~/.pyenv/versions
git clone https://github.com/wbolster/pyenv-no-global-pip.git no-global-pip
```

Make sure the `~/.pyenv/versions` file contains `no-global-pip` as the first item. For example, to have multiple Python versions available from any terminal without any extra setup, use something like this:

```
no-global-pip
3.8-dev
3.6.8
2.7-dev
```

Make sure to run `pyenv rehash` after changing the file.
