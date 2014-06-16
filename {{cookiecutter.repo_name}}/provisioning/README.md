ansible-django
==============

Upgrading guest additions
-------------------------

To keep the VirtualBox guest additions up-to-date, use the
[vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest) plugin.


TODO:
-----

Include reference to "First 5 min on server" ansible blog post
    http://practicalops.com/my-first-5-minutes-on-a-server-with-ansible.html
    http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers

`supervisor` cannot manage `redmon` at the moment (tasks commented out)

look into monit

Write about adding a rule to ~/.ssh/config to avoid host error

There is a log dir created for the app, /var/log/{{ '{{' }}project_name{{ '}}' }}


Troubleshooting
---------------

If you run into this error right after `vagrant up`:

```
TASK: [update APT package cache and aptitude safe-upgrade] ********************
fatal: [127.0.0.1] => SSH encountered an unknown error during the connection.
We recommend you re-run the command using -vvvv, which will enable SSH debugging
output to help diagnose the issue
```

Then just remove the line starting with `[127.0.0.1]:2222` and run
`vagrant provision`.  If the error still persists, try Google or open an issue.
