In order to be able to connect from the Ansible container to the target container, we need to create a private + public SSH key pair on Ansible and copy the public key to the target machine.
 
For that, let us exit from the target container
 
`exit`{{execute HOST1}}
 
and enter the ansible container again.
 
`a`{{execute HOST1}}
 
On the ansible system, let us generate a SSH key pair like follows:
`ssh-keygen -t rsa`{{execute HOST1}}
 
Just keep the defaults, click into the Terminal and press return three times.
 
This will generate ~/.ssh/id_rsa.pub and ~/.ssh/id_rsa on the ~/.ssh directory:
 
`ls -ltr ~/.ssh`{{execute HOST1}}