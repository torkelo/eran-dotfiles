# How to setup my Macbook Pro

This document shall be a list of notes so that I remember all steps taken in order to get up to development speed with my Macbook Pro.

## In App Store:

* Install XCode (Important!)
* Install Mou
* Install Dropbox
* Install Evernote
* Install Skype

## In Browser
* Install MacVim: http://code.google.com/p/macvim/
* Install MySQL: http://www.mysql.com/downloads/mysql/
  * Also install the PreferencePane, comes with the same package
  * Start MySQL Server
  * Change root password: http://dev.mysql.com/doc/refman/5.5/en/resetting-permissions.html
* Install PostgreSQL: http://www.postgresql.org/download/macosx/
* Install Sequel Pro: http://www.sequelpro.com/download/
* Install Graphviz: http://www.graphviz.org/Download_macos.php

## In terminal::

    # install homebrew
    /usr/bin/ruby -e "$(curl -fsSL https://raw.github.com/gist/323731)"
    brew install autojump
    brew install graphviz

	# install pip
    sudo easy_install pip

	# install virtualenv
	sudo pip install virtualenv
	sudo pip install virtualenvwrapper
	export WORKON_HOME=~/Envs
	source /usr/local/bin/virtualenvwrapper.sh

## Create files

**~/.bash_profile**::

    # Get the aliases and functions
    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi

**~/.bashrc**::
    
    # git
    export GIT_SSL_NO_VERIFY=true 

    # virtualenvwrapper
    export WORKON_HOME=~/Envs
    source /usr/local/bin/virtualenvwrapper.sh

    # MacVim
    VIM_APP_DIR=/Applications

	# MySQL
	export PATH=$PATH:/usr/local/mysql/bin/
    export DYLD_LIBRARY_PATH=$DYLD_LIBRARY_PATH:/usr/local/mysql/lib/ 
    alias start_mysql="/Library/StartupItems/MySQLCOM/MySQLCOM start"
    alias stop_mysql="/Library/StartupItems/MySQLCOM/MySQLCOM stop"

    # Setting for the new UTF-8 terminal support in Lion
    export LC_CTYPE=en_US.UTF-8
    export LC_ALL=en_US.UTF-8

    # for autojump
    if [ -f `brew --prefix`/etc/autojump ]; then
         . `brew --prefix`/etc/autojump
    fi

## In terminal::

	# install global packages used by all virtualenvs
	sudo pip install ipython
	sudo pip install ipdb
	sudo pip install mysql-python
	sudo pip install pillow

## Misc

* If you need graphviz in one of your venvs, try ``pip install pygraphviz``.
  It will fail but you will see a pygraphviz folder in your 
  ``~/Envs/envname/build/`` folder. Open it's ``setup.py`` and uncomment
  the lines for OSX. Try ``pip install`` again.
* sudo nano /usr/local/bin/mvim and make sure that the line with the variable
  is commented out and we use the variable set in .bashrc
* You might need to change the ``default-storage-engine`` in your
  ``/etc/my.cnf`` to ``MyISAM``.