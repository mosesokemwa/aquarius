### Overview

``onedrive-d`` is a Microsoft OneDrive client on Linux platforms. It allows a Linux user to sync with one or more OneDrive Personal account by synchronizing each remote OneDrive repository with a designated local directory. Note that OneDrive for Business is not supported (see issue #1).

#### Pre-requisites

``onedrive-d`` is written in Python 3 and does NOT run under Python 2.x. The package is tested for the following Python versions: ``3.2``, ``3.3``, ``3.4``, ``3.5-dev``.

To check if you have the correct Python interpreter, run

    $ python3 --version
    
It is suggested that you install the latest version of pip3 and setuptools:

    # Download the latest pip package from source
    $ wget -O- https://bootstrap.pypa.io/get-pip.py | sudo python3

    # Use pip3 to upgrade setuptools
    $ sudo pip3 install --upgrade setuptools
It is very important that your system hardware clock is set to UTC. Refer to ``man tzconfig`` for more details.

#### Install

After properly setting up pre-requisites, run the following command to install the package:

    # use sudo to install the package system-wide
    $ python3 setup.py build
    $ sudo python3 setup.py install
Note: GUI will be implemented in a separate package as an ``onedrive-d`` extension.

#### Uninstall

You will need ``pip3`` to properly uninstall the package. Refer to Pre-requisites section for how to get the latest ``pip3``.

    $ sudo pip3 uninstall onedrived

#### Support

Please beware that the program comes with absolutely NO WARRANTY, and resources for tech support are extremely limited.

To report a bug or ask a question, create an issue on the repository.

For the original document please refer to [github onedrive repository](https://github.com/xybu/onedrive-d#onedrive-d)