simply type this in your CLI terminal

    apt-get install mysql mysql-server

to activate the process use:

        chkconfig mysqld on
to start the process system wide:

    service mysqld start
afterwards set the MySQL root password:
    
    mysqladmin -u root password 'new-password' (with the quotes)