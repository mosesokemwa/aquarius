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


### Setting Up The Project
Before we actually start the project, make sure you have ``git`` installed. It's available via package installation on most systems. If it isn't for yours, follow the directions on git-scm to install via source (not that difficult).

Let's start the project via django-admin:

    $ django-admin.py startproject myproject
This creates the myproject directory. Don't go there yet.

### Source Control Using Git
If you havent set up ``git`` yet you could refer to [setting up git](https://github.com/mussaimo/aquarius/blob/master/git.md)

Our current directory should show two directories: env and myproject. Since we'll be tracking both of these in git, we'll initialize our repository here using:

    $ git init
This creates a git repository in the current directory. Lets stage all of our files to git to be committed.

    $ git add .
Now we actually commit them to our new repo:

    $ git commit -a -m 'Initial commit of myproject'
If you plan on using a service like GitHub or Bitbucket, now would be a good time to push to them.

## Advanced django settings
### Using South for Database Migrations
One of the most frustrating things in a vanilla Django install is managing changes to models and the associated changes to the database. With the help of South, you can realistically create an entire application without ever writing database specific code. Changes to your models are detected and automatically made in the database through a migration file that South creates. This lets you both migrate the database forward for your new change and backwards to undo a change or series of changes. It makes your life so much easier, it's a wonder it's not included in the Django distribution (there has been some talk of including a database migration tool in Django, but it hasn't happened yet).

Still under our ``(env)`` virtualenv environment, install South like so:

    $ pip install south
We setup South by adding it to our INSTALLED_APS in the settings.py file for the project. Add that now, as well as your database settings for the project, then run python manage.py syncdb. You'll be prompted for a superuser name and password (which you can go ahead and enter). More importantly, South has setup the database with the tables it needs.

You may have noticed that we just ran ``syncdb`` without having adding an app to the project. We do this first so that South is installed from the beginning. All migrations to our own apps will be done using South, including the initial migration.

Since we've just made some pretty big changes, now would be a good time to commit to ``git``. You should get used to committing frequently, as the more granular the commit, the more freedom you have in choosing something to revert to if things go wrong.

To commit, first add any untracked files:

    $ git add .
Git users may notice I'm not adding specific files but rather everything under our main directory. That's because, to this point, there isn't anything we don't want to commit. Let's commit our changes using:

    $ git commit -a -m 'Added South for database migrations'

### Creating Our App
Use ``manage.py`` to create an app in the normal way ``(python manage.py startapp myapp)`` and add it as an ``INSTALLED_APP.`` The first thing we'll do, before adding models, is tell South we want to use it for migrations:

    $ python manage.py schemamigration myapp --initial
This creates a migration file that can be used to apply our changes (if we had any) and also revert them. We use the migration file to migrate the database changes (even though there are none) using :

    $ python manage.py migrate myapp
South is smart enough to know where to look for migration files, as well as remember what was the last migration we did. You can specify individual migration files, but it's usually not necessary.

When we eventually make changes to our model, we ask South to create a migration using:

    $ python manage.py schemamigration myapp --auto
This will inspect the models in myapp and automatically add, delete, or modify the database tables accordingly.

### Our Development Area
One of the things you should get used to is doing development in a separate area, not where you're serving your files from, for obvious reasons. Git makes this simple and also helps with deployments. Create a directory somewhere other than where myproject is installed for your development area (I just call it dev).

In your development directory, clone the current project using git:

    $ git clone /path/to/my/project/
Git will create an exact copy of the entire repository. All changes, branches, and history will be available here. From here on out, you should be working from your development directory.

Since branching with git is so easy and cheap, create branches as you work on new, orthogonal changes to your site. Do so by typing:

    $ git checkout -b <branchname>
Which will both create a new branch named and check it out. Almost all of your development should be done on a branch, so that master mimics the current production master and can be used for recovery at any time.

### Using Fabric for Deployment
So we have the makings of a Django application. How do we deploy it? Thanks to readers of the blog, I'm a recent convert to Fabric, a fantastic tool perfectly suited to our deployment needs. Install Fabric to our virtualenv like so:

    $ pip install fabric
Fabric expects a file , fabfile.py, to define all of the actions we can take. Let's create that now. Put the following in your fabfile.py in the myproject directory:

    from fabric.api import local

    def prepare_deployment(branch_name):
        local('python manage.py test myapp')
        local('git add -p && git commit')
        local('git checkout master && git merge ' + branch_name)
        
This will run the tests, commit your branch change, and merge them into master. At this point, a simple "git pull" in your production area becomes your deployment. Lets add a bit more to actually deploy. Add this to your fabfile.py:

    from fabric.api import lcd

    def deploy():
        with lcd('/path/to/my/prod/area/'):
            local('git pull /my/path/to/dev/area/')
            local('python manage.py migrate myapp')
            local('python manage.py test myapp')
            local('/my/command/to/restart/webserver')
            
This will pull your changes from the development master branch, run any migrations you've made, run your tests, and restart your webserver. All in one simple command from the command line. If one of those steps fails, the script stops and reports what happened. Once you fix the issue, there is no need to run the steps manually. Simply rerun the deploy command and all will be well.

So now that we have our fabfile.py created, how do we actually deploy? Simple. Just run:

    $ fab prepare_deployment:<your_branch_name>
    $ fab deploy
    
Technically, these could be combined into a single command, but I find it's better to explicitly prepare your deployment and then deploy as it makes you focus a bit more on what you're doing.

## Happy coding