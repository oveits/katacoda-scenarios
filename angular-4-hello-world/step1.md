#### Step 1: Start CentOS Container

`docker run -it -p 4200:4200 centos bash`{{execute}}

#### Step 2: Install Angular CLI

On the container:

`yum install -y epel-release`{{execute}}

Install NodeJS:

`yum install -y nodejs`{{execute}}

Install Angular CLI:

`npm install -g @angular/cli`{{execute}}

Check Angular CLI Version:

`ng -v`{{execute}}

Output:
<pre>    _                      _                 ____ _     ___
   / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
  / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
 / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
/_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
               |___/
@angular/cli: 1.1.0
node: 6.10.3
os: linux x64
</pre>

#### Step 3: Create new Project

Now let us create a project:

`cd /localdir && \
ng new my-project-name  && \
cd my-project-name`{{execute}}

#### Step 4: Start Service

`ng serve --host 0.0.0.0`{{execute}`

Output:
`> my-project-name@0.0.0 start /localdir/my-project-name
> ng serve

** NG Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200 **
Hash: 46f1654c27ac4755fbcd
Time: 9010ms
chunk    {0} polyfills.bundle.js, polyfills.bundle.js.map (polyfills) 158 kB {4} [initial] [rendered]
chunk    {1} main.bundle.js, main.bundle.js.map (main) 5.29 kB {3} [initial] [rendered]
chunk    {2} styles.bundle.js, styles.bundle.js.map (styles) 10.5 kB {4} [initial] [rendered]
chunk    {3} vendor.bundle.js, vendor.bundle.js.map (vendor) 2.11 MB [initial] [rendered]
chunk    {4} inline.bundle.js, inline.bundle.js.map (inline) 0 bytes [entry] [rendered]
webpack: Compiled successfully.`


`docker run -it -p 8080:8080 -v $(pwd):/localdir ubuntu bash`{{execute}}

`apt-get update && apt-get install -y git npm`{{execute}}




`git clone https://github.com/edc4it/angular-webpack-seed.git && cd angular-webpack-seed`{{execute}}

Workaround for Ubuntu:
`ln -s nodejs /usr/bin/node`{{execute}}

Seems to be needed for npm install to be successful:
`npm i zone.js`{{execute}}

`npm install`{{execute}}


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

Needed for yarn start:
`npm i -g yarn`{{execute}}

Then:
`yarn start`{{execute}}

This should yield the error:
ERROR in multi (webpack)-dev-server/client?http://localhost:8080 ./src/main.ts
Module not found: Error: Can't resolve './src/main.ts' in '/localdir/angular-webpack-seed'
 @ multi (webpack)-dev-server/client?http://localhost:8080 ./src/main.ts
 
`touch src/main.ts`{{execute}}


> NEEDED or already covered with the npm install?
`npm install -g yarn`{{execute}}

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
