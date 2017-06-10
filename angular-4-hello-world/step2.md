Install via quickstart (requires low memory)

#### Step 1: Start CentOS Container

`docker run -it -p 3000:3000 centos bash`{{execute}}

#### Step 2: Install Angular CLI

On the container:

`yum install -y epel-release`{{execute}}

Install git and NPM:

`yum install -y git npm`{{execute}}

`npm -v`{{execute}}

Clone the Quickstart Template:
`git clone https://github.com/angular/quickstart; cd quickstart`{{execute}}

Install packages via NPM:

`npm i`

Start Service:

`npm start`{{execute}}

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

`ng new my-project-name  && \
cd my-project-name`{{execute}}

#### Step 4: Start Service

`ng serve --host 0.0.0.0`{{execute}`



The first step is to install the [Github](https://wiki.jenkins-ci.org/display/JENKINS/GitHub+Plugin) and [Pipeline](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Plugin) plugins, since we will use a Pipeline to clone and build a Github repository.

#### Task: Install Plugins

1. Within the Dashboard, select **Manage Jenkins** on the left.
2. On the Configuration page, select **Manage Plugins**.
3. Manage Plugins page will give you a tabbed interface. Click **Available** and wait three seconds to view all the Jenkins plugins that can be installed.
4. Using the search box, search for **Github plugin** and choose the plugin via checkbox.
5. While on this page, search for **Pipeline** and choose the plugin via checkbox.
6. Click **Install without Restart** at the bottom.
7. The plugins will now be downloaded and installed. Once complete, click the link **Go back to the top page**.

Your Jenkins server can now be configured to build a 'hello world' application using pipelines.
