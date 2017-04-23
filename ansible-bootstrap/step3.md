Let us exit from the ansible container
 
`exit`{{execute HOST1}}
 
and enter the target container:
 
`t`{{execute HOST1}}
 
In our case, the target is an Ubuntu machine with no SSH server installed. Let us do that now:
 
`apt-get update; apt-get install -y openssh-server;service ssh start`{{execute HOST1}}