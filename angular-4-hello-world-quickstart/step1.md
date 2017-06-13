Install via quickstart (requires low memory)

#### Step 1: Start CentOS Container

`docker run -it -p 8080:3000 centos bash`{{execute}}
or skip Step 1 and 2 for starting with a Docker image 

#### Step 2: Install Git and NPM

On the container we install git and npm from the EPEL release:

`yum install -y epel-release git npm`{{execute}}

`npm -v`{{execute}}

The version should be 3 or larger.



