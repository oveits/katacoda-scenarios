This is a fork of https://github.com/oveits/jenkins-scenarios of Ben Hall, upgraded from Jenkins 1.651.1 to 2.46.2.

We will prepare an environment with a Jenkins server running as a Docker Container.

First we start the container in detached mode with a while loop. This allows us to prepare the Jenkins environment before we start the application:

`docker run -d -u root --rm --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    --entrypoint bash \
    jenkins:2.46.2-alpine \
    -c "while true; do sleep 60; echo keepalive; done"`{{execute}}
    
With the next command, we clone a Jenkins Home into the container, before we start the Jenkins application. The Jenkins Home has been prepare to allow us to use Jenkins without any login:

`docker exec -d jenkins \
    bash -c 'git clone https://github.com/oveits/jenkins_home_alpine \
        && export JENKINS_HOME=$(pwd)/jenkins_home_alpine \
        && java -jar /usr/share/jenkins/jenkins.war &'`{{execute}}

After a minute or so, we should see that the jenkins.war is started:

`docker exec jenkins ps -ef`{{execute}}

#### Load Dashboard

You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.

> REMOVE the rest after the above commands have been tested!

With  check whether the application is up and running: 

All plugins and configurations get persisted to the host at _/root/jenkins_. Port 8080 opens the web dashboard, 50000 is used to communicate with other Jenkins agents. Finally, the image has an alpine base to reduce the size footprint.

#### Load Dashboard

You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.


`docker run -d -u root --rm --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    --entrypoint bash \
    jenkins:2.46.2-alpine \
    -c "while true; do sleep 60; echo keepalive; done"`{{execute}}
    
    
`docker exec -d jenkins \
    bash -c 'git clone https://github.com/oveits/jenkins_home_alpine \
        && export JENKINS_HOME=$(pwd)/jenkins_home_alpine \
        && java -jar /usr/share/jenkins/jenkins.war &'`{{execute}}

`docker exec jenkins ps -ef`{{execute}}



`([ -d "jenkins_home" ] || mkdir jenkins_home) && cd jenkins_home`{{execute}}

Not as root, should run indefinetely:

(does not work: Why?)
`docker rm jenkins 2>/dev/null; \
 docker run -it --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v $(pwd):/var/jenkins_home \
    --entrypoint bash \
    jenkins:2.46.2-alpine`

As root with mapped volume: 

   
`docker run -d -u root --rm --name jenkins \
     -p 8080:8080 -p 50000:50000 \
     -v $(pwd):/var/jenkins_home \
     --entrypoint /bin/bash \
     jenkins:2.46.2-alpine \
     -c "while true; do echo hallo; sleep 60; done"`{{execute}}
     
As jenkins without mapped volume:

`docker run -d --rm --name jenkins \
     -p 8080:8080 -p 50000:50000 \
     --entrypoint /bin/bash \
     jenkins:2.46.2-alpine \
     -c "while true; do echo hallo; sleep 60; done"`{{execute}}

> Remove:
`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v $(pwd):/var/jenkins_home \
    --entrypoint bash \
    jenkins:2.46.2-alpine`{{execute}}
    
We attach to the container:
    
`docker exec -it jenkins bash`{{execute}}

Let us initialize Jenkins:
    
`cd /var/jenkins_home; /usr/local/bin/jenkins.sh &`{{execute}}

After a minute or two, a config.xml file is created:

`ls -l config.xml*`{{execute}}

For the purpose of this tutorial, we will disable security, so we do not need to go through the hassle of creating an admin user with the initial secret key:

`sed -i.bak -e '/useSecurity/s/true/false/' config.xml`{{execute}}

We have kept the original file as a reference. Let us inspect the difference:

`diff config.xml.bak config.xml`{{execute}}

We need to restart the jenkins java application for the change to take effect:
`P=$(ps -ef | grep jenkins | grep jar | grep -v grep | awk '{ print $2}' ); kill $P`{{execute}}

And let us start the jenkins process again:

`java -jar /usr/share/jenkins/jenkins.war`{{execute}}





    
    


Let us prepare a Jenkins Home folder, where the admin user is pre-installed:

`git clone https://github.com/oveits/jenkins_home_alpine jenkins_home && cd jenkins_home`{{execute}}

Now let us download and run a Jenkins server as a Docker Container like follows:

Let us download and run a Jenkins server as a Docker Container like follows:

mkdir jenkins_home; cd jenkins_home

`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v $(pwd):/var/jenkins_home \
    jenkins:2.46.2-alpine`{{execute}}
    
For the purpose of this tutorial, we will disable security, so we do not need to go through the hassle of creating an admin user with the initial secret key:

`sed -i.bak -e '/useSecurity/s/true/false/' config.xml`{{execute}}

We need to restart the jenkins java application for the change to take effect:
P=$(ps -ef | grep jenkins | grep jar | grep -v grep | awk '\''{ print $2}'\'' ); kill $P

  

This will create some file jenkins needs in the jenkins_home directory. Those changes should be synched to the host system, so we should be able to see them on the system:

ls

cat config.xml | grep useSecurity

We can see, that the default is, to run Jenkins with security switched on. For the purpose of this tutorial, we will disable security, so we do not need to go through the hassle of creating an admin user with the initial secret key:

sed -i.bak -e '/useSecurity/s/true/false/' config.xml

We have kept the original file as a reference. Let us inspect the difference:

diff config.xml config.xml.bak

For the changes to have an effect, we restart the jenkins application.

Unfortunately, if we restart the container like follows, the config.xml is re-initialized.


`docker stop jenkins; docker start jenkins`{{execute}}

Therefore we need to kill the  


docker image:

`docker exec jenkins sed -i.bak '/useSecurity/s/true/false/' /var/jenkins_home/config.xml`{{execute}}

For this change to take effect, we restart Jenkins:

`docker stop jenkins; docker start jenkins`{{execute}}
    
>>>REMOVE    

`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v /root/jenkins:/var/jenkins_home \
    jenkins:1.651.1-alpine`{{execute}}
    
Latest version (requires login procedure)

`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v /root/jenkins:/var/jenkins_home \
    jenkins:2.46.2-alpine`{{execute}}
<<<<REMOVE

You can view the status using `docker ps`{{execute}}.

All plugins and configurations get persisted to the host at _/root/jenkins_. Port 8080 opens the web dashboard, 50000 is used to communicate with other Jenkins agents. Finally, the image has an alpine base to reduce the size footprint.

#### Load Jenkins Web Page

You can load the Jenkins' web page via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

In the next steps, you'll create an admin user and log in.
