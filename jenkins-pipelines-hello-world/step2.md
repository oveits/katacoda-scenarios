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
