Install via quickstart (requires low memory)

#### Step 1: Start CentOS Container

`docker run -it -p 8080:3000 centos bash`{{execute}}

#### Step 2: Install Git and NPM

On the container:

`yum install -y epel-release`{{execute}}

Install git and NPM:

`yum install -y git npm`{{execute}}

Alternatively we can run the docker container with npm and git already installed:

`docker run -it -p 8080:3000 oveits/centos_npm_git bash`{{execute}}

`npm -v`{{execute}}

#### Step 3: Clone Quickstart Template

Clone the Quickstart Template:
`git clone https://github.com/angular/quickstart; cd quickstart`{{execute}}

Install packages via NPM:

`npm i`{{execute}}

To start over again from here, you can start the Docker container from an image, 
where all the above steps have been accoplished already:

`docker run -it -p 8080:3000 oveits/angular_hello_world:centos bash`{{execute}}

Start Service:

`npm start &`{{execute}}

#### Load Dashboard

You can load the angular application on the dashboard or via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ or by clicking the dashboard tab on the right (note: sometimes, you need to wait a few seconds and press "display port" at this point).

#### Change Component

With following example, we can see that a change in a file is detected immediately and the Appliction is changed accordingly:

`sed -r -i 's/Angular/World/g' src/app/app.component.ts`{{execute}}

In the Dashboard or the Browser, where you have opened the Client, 
"Hello Angular" is automatically exchanged by "Hello World". There is no need 
to reload the browser manually. You just need to wait for some seconds, 
depending on your Internet speed.

To toggle back and to 'Hello Anglar', you can issue the command 
`sed -r -i 's/World/Angular/g' src/app/app.component.ts`{{execute}}
.


