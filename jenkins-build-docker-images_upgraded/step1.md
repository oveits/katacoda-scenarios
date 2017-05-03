Let us prepare a Jenkins Home folder, where the admin user is pre-installed:

`git clone https://github.com/oveits/jenkins_home_alpine && cd jenkins_home_alpine`{{execute}}

Now let us download and run a Jenkins server as a Docker Container like follows:

Let us download and run a Jenkins server as a Docker Container like follows:

`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v $(pwd):/var/jenkins_home \
    jenkins:2.46.2-alpine`{{execute}}
    
For the purpose of this tutorial, we disable security, so we do not need to go through the hassle of creating an admin user with the initial secret key, so we just disable security:

`docker exec jenkins sed -i.bak '/useSecurity/s/true/false/' /var/jenkins_home/config.xml`{{execute}}

For this change to take effect, we restart Jenkins:

`docker stop jenkins; docker start jenkins`
    
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
