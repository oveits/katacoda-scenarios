Now let us perform the first remote shell command.

Now, since the target knows about the Ansible host's public SSH key, we are ready to connect from the Ansible host to our target:
 
`ansible all -i 'target,' -m shell -a "echo hello world\! > testfile"`{{execute HOST1}}

This time the module is a "shell" instead of a "ping" and the module's argument is a echo hello world command redirected into a test file. 

We should get a feedback that looks like follows:

<pre>
<span style="color: green">target | SUCCESS | rc=0 &gt;&gt;</span>
</pre>

Now let us check on the target, whether the test file really has been created:

We log into the target: 

`exit`{{execute HOST1}}
 
`t`{{execute HOST1}}

And print out the contends of the test file:

`cat ~/testfile`{{execute HOST1}}

The output should be 

<pre>
hello world!
</pre>

> Success!