### About Git

Git is a distributed version control system released to the public in 2005. The program allows for non-linear development of projects, and can handle large amounts of data effectively by storing it on the local server. 

**This tutorial will cover two ways to install Git.**

#### How to Install Git with Apt-Get

Installing Git with ``apt-get`` is a quick and easy process. The program installs on the virtual private server with one command:

    sudo apt-get install git-core 
After it finishes downloading, you will have Git installed and ready to use.

#### How to Install Git from Source
If you are eager to download the most recent version of Git, it is generally a good idea to install it from the source.

Quickly run ``apt-get update`` to make sure that you download the most recent packages to your VPS.

    sudo apt-get update
Prior to installing Git itself, download all of the required dependancies:

    sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev build-essential  
Once they are installed, you can download the latest version of Git from the google code page.

    wget https://git-core.googlecode.com/files/git-1.8.1.2.tar.gz
After it downloads, untar the file and switch into that directory:

    tar -zxf git-1.8.1.2.tar.gz
    cd git-1.8.1.2 

If you want to do a global install, install it once as yourself and once as root, using the sudo prefix:

    make prefix=/usr/local all 
    sudo make prefix=/usr/local install  

If you need to update Git in the future, you can use Git itself to do it.

    git clone git://git.kernel.org/pub/scm/git/git.git 

### How to Setup Git
After Git is installed, whether from ``apt-get`` or from the source, you need to copy your username and email in the gitconfig file. You can access this file at ``~/.gitconfig.``

Opening it following a fresh Git install would reveal a completely blank page:

    sudo nano ~/.gitconfig 
You can use the follow commands to add in the required information.

    git config --global user.name "NewUser" 
    git config --global user.email newuser@example.com 

You can see all of your settings with this command:

    git config --list

If you avoid putting in your username and email, git will later attempt to fill it in for you, and you may end up with a message like this:

    [master 0d9d21d] initial project version
    Committer: root
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author