Let us copy the public key of the Ansible host to a shared folder, we have prepared beforehand.
 
`cp ~/.ssh/id_rsa.pub /shared_volume/ansible_id_rsa.pub`{{execute HOST1}}

> In situations, where no shared_volume is available, it is sufficient to copy the content of the file to the clipboard, so we can paste it to the appropriate file on the target.
 
# Append public key to target's authorized_keys file

In order to inform the target about the ansible host's public SSH key, we need to connect to the target again:
 
`exit`{{execute HOST1}}
 
 
`t`{{execute HOST1}}

The public SSH key of the Ansible host needs to be appended to the list of authorized_keys:
 
`[ ! -d ~/.ssh ] && mkdir ~/.ssh; cat /shared_volume/ansible_id_rsa.pub >> ~/.ssh/authorized_keys`{{execute HOST1}}

Let us review the resulting file:

`cat ~/.ssh/authorized_keys`{{execute HOST1}}

It should contain a line similar to following:

<pre>
ssh-rsa AAAAB3NzaC1yc2EAA...TtW8ZK5RCND/CR root@9c476c271d4f
</pre>


