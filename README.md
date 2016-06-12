# virtualenv-mv

This is a quick and dirty tool used to move (rename) directories created by virtualenv and/or venv.

Right now, the script just replaces the current path with the destination path in all of the important files. This includes the contents of the activate scripts (e.g. `bin/activate`, `bin/activate.csh`, `bin/activate.fish`), the shebang on scripts (e.g. `bin/easy_install`, `bin/easy_install-3.4`, `bin/pip`, `bin/pip3`, `bin/pip3.4`, `bin/wheel`) and the records within `RECORD` files (e.g. `lib/python3.4/site-packages/wheel-0.24.0.dist-info/RECORD`, `lib/python3.4/site-packages/setuptools-18.2.dist-info/RECORD`, `lib/python3.4/site-packages/pip-7.1.2.dist-info/RECORD`).

It does not update the SHA256 hashes stored in RECORD for files that have had their shebangs modified. These hashes are only verified during installation. So far as I can tell, they serve no further purpose. See [PEP-0427](https://www.python.org/dev/peps/pep-0427/#the-dist-info-directory).

It also has some basic error handling and will leave an untouched backup of the virtualenv in the event on an error.

A few things on the wish list: submit the package to PyPi for easy installation via `pip` and consider the ability to repair virtualenvs that have already been moved incorrectly.

Installation
------------

To install `virtualenv-mv` for the current user (assuming directory is on your PATH):

    install virtualenv-mv ~/.local/bin

To install `virtualenv-mv` for all users:

    sudo install virtualenv-mv /usr/local/bin

Usage
-----

Use `virtualenv-mv` like you would use a simple implementation of `mv` (without any options).

	Usage: virtualenv-mv [OPTION]... SOURCE DEST
	  or:  virtualenv-mv [OPTION]... SOURCE... DIRECTORY
	Rename SOURCE to DEST, or move SOURCE to DIRECTORY.

Note that this tool cannot currently help if you've already moved the directory away from the directory it was created in with another tool.

License
-------

Copyright (c) 2015 Six <brbsix@gmail.com>

Licensed under the GPLv3 license.
