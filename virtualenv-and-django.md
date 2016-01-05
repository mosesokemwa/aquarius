### Installing virtualenv

To install ``virtualenv`` you need to run the following command in your terminal 

    $ sudo apt-get install python-virtualenv

once installed you need to create a virtual environment in your projects folder

    $ virtualenv env
Now that we have a virtualenv environment, we need to activate it. This sets up various environment variables to effectively bypass the system's Python install and uses our env one instead. Activate like so:

    $ source ./env/bin/activate
You should see ``(env) $`` at your prompt, letting you know that you're running under the 'env' virtualenv install. At any time, just type:

    $ deactivate
to stop using virtualenv.

### Installing Django
"Wait, 'Installing Django'? I already have Django installed!" Fantastic. You aren't going to use it. Instead, we'll use one managed by virtualenv that can't be messed up by other users (or yourself) working elsewhere on the machine. To install Django under virtual env, just type:

    $ pip install django
This should give you the latest version of Django which will be installed in your virtualenv area. You can confirm this by doing:

    $ which django-admin.py
Which should report an area under our env directory. If it doesn't, make sure you see ``(env)`` at your prompt. If you don't, you didn't ``$ source ./env/bin/activate``