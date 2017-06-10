Install via quickstart (requires low memory)

#### Step 1: Start CentOS Container

`docker run -it -p 8080:3000 centos bash`{{execute}}

#### Step 2: Install Angular CLI

On the container:

`yum install -y epel-release`{{execute}}

Install git and NPM:

`yum install -y git npm`{{execute}}

`npm -v`{{execute}}

Clone the Quickstart Template:
`git clone https://github.com/angular/quickstart; cd quickstart`{{execute}}

Install packages via NPM:

`npm i`{{execute}}

Start Service:

`npm start &`{{execute}}

#### Load Dashboard

You can load the angular application on the dashboard or via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ or by clicking the dashboard tab on the right (note: sometimes, you need to wait a few seconds and press "display port" at this point).



