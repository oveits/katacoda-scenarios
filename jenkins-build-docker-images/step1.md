This is a fork of https://github.com/oveits/jenkins-scenarios of Ben Hall, upgraded from Jenkins 1.651.1 to 2.46.2.

We will prepare an environment with a Jenkins server running as a Docker Container.

First we start the container in detached mode with a tail to a log file we will create and use later:

`docker run -d -u root --rm --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    --entrypoint bash \
    jenkins:2.46.2-alpine \
    -c "tail -F /jenkins.log"`{{execute}}
    
With the next command, we clone a Jenkins Home directory into the container, before we start the Jenkins application. The Jenkins Home directory has been prepared to allow us using Jenkins without any login:

`docker exec -d jenkins \
    bash -c 'git clone https://github.com/oveits/jenkins_home_alpine \
        && export JENKINS_HOME=$(pwd)/jenkins_home_alpine \
        && java -jar /usr/share/jenkins/jenkins.war 2>&1 1>/jenkins.log &'`{{execute}}

After a minute or so, we should see that the jenkins.war is started:

`docker exec jenkins ps -ef`{{execute}}

#### Load Dashboard

You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/  or by clicking the dashboard tab on the right.

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.
