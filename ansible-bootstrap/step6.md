Now, since the target knows about the Ansible host's public SSH key, we are ready to connect from the Ansible host to our target:

`exit`{{execute HOST1}}
 
 
`a`{{execute HOST1}}
 
 
Now we test the connection, that had failed previously:
 
`ansible all -i 'target,' -m ping`{{execute HOST1}}
 
This time we get following output:
<pre>
<span style="color: green">target | SUCCESS => {
    "changed": false,
    "ping": "pong"
}</span>
</pre>

> Success!