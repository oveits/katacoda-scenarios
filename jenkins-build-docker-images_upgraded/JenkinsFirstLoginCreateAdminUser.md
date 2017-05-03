As described in the Web Page, we need to access the Linux console of the Jenkins container and read the access key from a file. Let us read the contents of the file into a variable named PASS:

`PASS=$(docker exec -i jenkins cat /var/jenkins_home/secrets/initialAdminPassword)`{{execute}}

cat /var/jenkins_home/
    
 like follows:


for our first log

Let us prepare a Jenkins Home folder, where the admin user is pre-installed:

`git clone https://github.com/oveits/jenkins_home_alpine && cd jenkins_home_alpine`{{execute}}

Now let us download and run a Jenkins server as a Docker Container like follows:

Let us download and run a Jenkins server as a Docker Container like follows:

`docker run -d -u root --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    -v `pwd`:/var/jenkins_home \
    jenkins:2.46.2-alpine`{{execute}}
    
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

#### Load Dashboard

You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.
