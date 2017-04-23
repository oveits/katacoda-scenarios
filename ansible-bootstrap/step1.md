To make our lives easier later, let us define the commands "a" and "t" for quickly connecting from the base system to the ansible and target container:

Connect to the Ansible container:
 
```a() { docker exec -it ansible bash -c "echo 'PS1='\''ansible# '\' >> /root/.bashrc; bash"; } ```{{execute HOST1}}
 
Connect to the Target container:
 
``` t() {  docker exec -it target bash -c "echo 'PS1='\''target# '\' >> /root/.bashrc; bash";  } ```{{execute HOST1}}
 
In this tutorial, we already have started an ansible and a target container in the background. However, they have been started in the background, and they need some time to become available. Repeat using a docker ps command to check, whether Docker containers named 'ansible' and 'target' have been started already:
 
`docker ps`{{execute HOST1}}
 
Repeat sending the command until it looks similar to
<pre>
CONTAINER ID      IMAGE                                   COMMAND                 CREATED         STATUS
            PORTS NAMES
c96e3a45e164      ubuntu:14.04                            "/bin/bash -c 'whi..."  11 seconds ago  Up 9 seconds target
caf61a258abb      williamyeh/ansible:ubuntu14.04-onbuild  "/bin/bash -c 'whi..."  13 seconds ago  Up 11 seconds ansible
</pre>

This should take no longer than 30 sec.
