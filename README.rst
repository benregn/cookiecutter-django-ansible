cookiecutter-django-ansible
=======================

A cookiecutter_ template for Django. Based on pydanny's `cookiecutter-django`_.

.. _cookiecutter: https://github.com/audreyr/cookiecutter
.. _cookiecutter-django: https://github.com/pydanny/cookiecutter-django

Features
---------

* For Django 1.6
* Twitter Bootstrap_ 3
* Settings management via django-configurations_
* Registration via django-allauth_
* User avatars via django-avatar_
* Basic caching setup
* Grunt build for compass and livereload
* Vagrant development environment
* (Almost) ready to deploy to `Digital Ocean`_
.. * Basic e-mail configurations for send emails via SendGrid_

.. _Bootstrap: https://github.com/twbs/bootstrap
.. _django-configurations: https://github.com/jezdez/django-configurations
.. _django-allauth: https://github.com/pennersr/django-allauth
.. _django-avatar: https://github.com/jezdez/django-avatar/
.. _Digital Ocean: https://www.digitalocean.com/
.. _SendGrid: https://sendgrid.com/


Constraints
-----------

* Only maintained 3rd party libraries are used.
* PostgreSQL everywhere
* Environment variables for configuration (This won't work with Apache/mod_wsgi).


Usage
------

Let's pretend you want to create a Django project called "redditclone". Rather than using `startproject`
and then editing the results to include your name, email, and various configuration issues that always get forgotten until the worst possible moment, get cookiecutter_ to do all the work.

First, get cookiecutter. Trust me, it's awesome::

    $ pip install cookiecutter

Now run it against this repo::

    $ cookiecutter https://github.com/benregn/cookiecutter-django-ansible.git

You'll be prompted for some questions, answer them, then it will create a Django project for you.


**Warning**: After this point, change 'Tomas Thor Jonsson', 'benregn', etc to your own information.

It prompts you for questions. Answer them::

    Cloning into 'cookiecutter-django'...
    remote: Counting objects: 550, done.
    remote: Compressing objects: 100% (310/310), done.
    remote: Total 550 (delta 283), reused 479 (delta 222)
    Receiving objects: 100% (550/550), 127.66 KiB | 58 KiB/s, done.
    Resolving deltas: 100% (283/283), done.

    project_name (default is "project_name is the title of the project.")? Reddit clone
    repo_name (default is "repo_name is used for describing the directory structure.")? reddit_clone
    author_name (default is "Your Name")? Tomas Thor Jonsson
    email (default is "Your email")? benregn@gmail.com
    description (default is "A short description of the project.")? A reddit clone.
    year (default is "2014")?
    domain_name (default is "example.com")?
    public_ssh_key_path (default is "~/.ssh/id_rsa.pub")?
    private_ssh_key_path (default is "~/.ssh/id_rsa")?
    version (default is "0.1.0")?


Enter the project and take a look around::

    $ cd reddit_clone/
    $ ls

Create a GitHub repo and push it there::

    $ git init
    $ git add .
    $ git commit -m "first awesome commit"
    $ git remote add origin git@github.com:benregn/redditclone.git
    $ git push -u origin master

Now take a look at your repo. Don't forget to carefully look at the generated README. Awesome, right?

Getting up and running
----------------------

The steps below will get you up and running with a local development environment.

**Install VirtualBox and Vagrant**

To get a local development machine running, you'll need VirtualBox and Vagrant.

* `Download VirtualBox`_ for your system and install it.
* `Download Vagrant`_ for you system and install it.

.. _Download VirtualBox: https://www.virtualbox.org/wiki/Downloads
.. _Download Vagrant: http://www.vagrantup.com/downloads.html

**Install ansible**

First step is to install ansible_.

.. _ansible: http://www.ansible.com/home

If you are on OSX you can use Homebrew::

    $ brew update
    $ brew install ansible

If not, ansible is available from PyPi via pip::

    $ sudo pip install ansible

Other installation methods are listed in the `ansible installation docs`_.

.. _ansible installation docs: http://docs.ansible.com/intro_installation.html

**Vagrant**

When you got ansible installled, you can run::

    $ vagrant up

When ansible finishes provisioning the VM, you should have a dev server running at `127.0.0.1:8000`_
and uwsgi/nginx server at `localhost:8080`_.

.. _127.0.0.1:8000: http://127.0.0.1:8000/
.. _localhost:8080: http://localhost:8080/

.. **Live reloading and Sass CSS compilation**

.. If you'd like to take advantage of live reloading and Sass / Compass CSS compilation you can do so with the included Grunt task.

.. Make sure that nodejs_ is installed. Then in the project root run::

..     $ npm install

.. .. _nodejs: http://nodejs.org/download/

.. Now you just need::

..     $ grunt serve

.. The base app will now run as it would with the usual ``manage.py runserver`` but with live reloading and Sass compilation enabled.

.. To get live reloading to work you'll probably need to install an `appropriate browser extension`_

.. .. _appropriate browser extension: http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-

.. It's time to write the code!!!

"Your Stuff"
-------------

Scattered throughout the Python and HTML of this project are places marked with "your stuff". This is where third-party libraries are to be integrated with your project.

Something you'd like to add?
---------------------------

I welcome pull requests, so just fork it :)
