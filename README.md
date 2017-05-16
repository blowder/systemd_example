# Example of simple Systemd service

Service template should have at least 3 sections:
- [Unit]
- [Service]
- [Install]

# [Unit]
> Description=Jetty aplication server.

Here we only add description of service.
# [Service]

>PIDFile=/var/run/jetty.pid

For track process id 
>WorkingDirectory=/home/username/.bin/jetty9/

Set up working directory for make sure that relative paths inside run.sh works fine.

>User=username
Group=groupname

User and group needed for script start

>ExecStart=/bin/bash /home/username/.bin/jetty9/run.sh

Full path to script. Also in case of bash script, script shoul start with line #!/bin/sh -

>TimeoutSec=1000

Timeout between start, stop, restart commands executions.

# [Install]
>WantedBy=multi-user.target

Define the runlevel for run on boot.

# How it works
Create file /etc/systemd/system/jetty.service
Copy content from this repo and edit paths and usernames.
And after than yoou should have ability to work with your service through systemctl
* systemctl start jetty
* systemctl stop jetty
* systemctl restart jetty

# Run on boot
For enable run on boot just execute command:
* systemctl enable jetty

For disable run on boot execute command:
* systemctl disable jetty
 
# For details:
* https://www.freedesktop.org/wiki/Software/systemd/