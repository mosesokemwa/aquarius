#### installing mysql linux
simply type this in your CLI terminal

    apt-get install mysql mysql-server

to activate the process use:

        chkconfig mysqld on
to start the process system wide:

    service mysqld start
afterwards set the MySQL root password:
    
    mysqladmin -u root password 'new-password' (with the quotes)

#### mysql GUI

    sudo apt-get install mysql-workbench

#### mysql_config not found
mysql-config is in a different package, which can be installed from (again, assuming debian / ubuntu):

    sudo apt-get install libmysqlclient-dev
