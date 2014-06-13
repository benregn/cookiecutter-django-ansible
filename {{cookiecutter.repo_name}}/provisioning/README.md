ansible-django
==============

Step-by-step
------------

1. have PSQL_USER, PSQL_DB_NAME, PSQL_PASSWORD in your environment
    * export PSQL_USER=username && export PSQL_DB_NAME=db_name && export PSQL_PASSWORD=your_password && export DATABASE_URL=postgres://$PSQL_USER:$PSQL_PASSWORD@localhost:5432/$PSQL_DB_NAME

2. configure synced folder in the Vagrantfile, change project_name, deploy and django_user

3. change following ansible vars:  root_dir, wsgi_path, logwatch_email, root_address, mailname, django_password
    * roles/rabbitmq/vars
        * rabbitmq.admin_password
        * rabbitmq.password
    * inventory/group_vars/all.yml
        * git_repo

4. run the provisioning once without uncommenting the `config.ssh.private_key_path = "/path/to/key"` line in the `Vagrantfile


Upgrading guest additions
-------------------------

To keep the VirtualBox guest additions up-to-date, use the [vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest) plugin.


TODO:
-----

Write a bit about removing vagrant insecure key task

Include reference to "First 5 min on server" ansible blog post

`supervisor` cannot manage `redmon` at the moment (tasks commented out)

Refactor each major service to be it's own role, e.g. nginx, postgres, redis etc. so they can be included as needed as git submodules.

Use cookiecutter to automate some of the setup for each new project?

Fabric or ansible deploy script

look into monit

Write about adding a rule to ~/.ssh/config to avoid host error

There is a log dir created for the app, /var/log/{{project_name}}


Troubleshooting
---------------

If you run into this error right after `vagrant up`:

```
TASK: [update APT package cache and aptitude safe-upgrade] ********************
fatal: [127.0.0.1] => SSH encountered an unknown error during the connection. We recommend you re-run the command using -vvvv, which will enable SSH debugging output to help diagnose the issue
```

Then just remove the line starting with `[127.0.0.1]:2222` and run `vagrant provision`
