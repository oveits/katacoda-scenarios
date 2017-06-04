`docker run -it -p 8080:8080 ubuntu bash`{{execute}}

`apt-get update && apt-get install -y git npm`{{execute}}
`npm install -g yarn`{{execute}}



`git clone https://github.com/edc4it/angular-webpack-seed.git && cd angular-webpack-seed`{{execute}}

`cat - << END  > index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Angular 4 Hello World</title>
</head>
<body>
<app>Loading app...</app>
</body>
</html>
END`{{execute}}

`cat - << END  > index.html
&lth;!DOCTYPE html&gth;
&lth;html lang="en"&gth;
&lth;head&gth;
    &lth;meta charset="UTF-8"&gth;
    &lth;title&gth;Angular 4 Hello World&lth;/title&gth;
&lth;/head&gth;
&lth;body&gth;
&lth;app&gth;Loading app...&lth;/app&gth;
&lth;/body&gth;
&lth;/html&gth;
END`{{execute}}

`cat - << END > index.html`{{execute}}

`cat - << END > index.html
bla
END`{{execute}}

Workaround for Ubuntu:
`ln -s nodejs /usr/bin/node`{{execute}}

`npm install`{{execute}}

> NOT NEEDED?
Install webpack locally, see https://stackoverflow.com/questions/29492240/error-cannot-find-module-webpack:
`npm install webpack webpack-dev-server`{{execute}}

Install html-webpack-plugin, see https://github.com/survivejs/webpack-book/issues/100
`npm install html-webpack-plugin --save-dev`{{execute}}

Install autoprefixer-core, see https://github.com/nDmitry/grunt-postcss/issues/3
`npm install autoprefixer-core`{{execute}}

`npm i html-loader typescript ts-loader tslint tslint-loader`{{execute}}

> NOT NEEDED? END



`yarn start`{{execute}}

This should yield `webpack: Failed to compile.`, since 


We will prepare an environment with a Jenkins server running as a Docker Container.

> Note: steps 1 to 3 can be skipped, if you want to head directly to the pipeline section. We will provide a pre-configured Jenkins image in step 4.

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

You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ or by clicking the dashboard tab on the right (note: sometimes, you need to wait a few seconds and press "display port" at this point).

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.
