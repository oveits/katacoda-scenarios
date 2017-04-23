# Summary

Let us summarize, what we have achieved so far:
> We have prepared the successful connection from an Ansible system to a target system by
> 1. installing an ssh server on the target
> 2. creating an SSH key pair on the Ansible system
> 3. copying the public key of the Ansible host to the target system
>
> We have tested the connection by using an Ansible "ping", which is an SSH connection from the Ansible host to the target, actually.

## Further Reading:

For more information about Ansible, see also following blogs on Ansible:

Posts of this series:

  1. [Ansible Hello World: Getting started with Playbooks and Inventories](https://oliverveits.wordpress.com/2015/11/09/it-automation-a-hello-world-example-using-ansible-on-docker/ "Ansible Hello World part 1")
      - with a comparison of Ansible vs. Salt vs. Chef vs. Puppet and a hello world example with focus on Playbooks (i.e. tasks), Inventories (i.e. groups of targets) and remote shell script execution.
  2. [Ansible Hello World: Templating](https://oliverveits.wordpress.com/2015/11/20/it-automation-part-ii-ansible-hello-world-for-templating/ "Ansible Hello World part 2")
  3. [Ansible Hello World: Graphical User Interface "Ansible Tower"](https://oliverveits.wordpress.com/2016/06/14/it-automation-part-iv-ansible-tower-hello-world-example/ "Ansible Hello World part 3") 
  
You might also be interested in this [Salt Hello World: Getting started with States and Node Groups](https://oliverveits.wordpress.com/2015/12/04/it-automation-part-iii-saltstack-hello-world-example/ "Salt Hello World")