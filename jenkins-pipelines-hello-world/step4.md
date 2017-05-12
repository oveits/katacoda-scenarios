We now will create our first Jenkins Pipeline project.

#### Task: Start pre-configured Jenkins, if you have skipped the previous steps

If you have skipped step 1 to 3, you now can start with a pre-configured Jenkins installation like follows:

Stop and remove any containers named "jenkins", if required:

`docker stop jenkins; docker rm jenkins`{{execute}}

`docker run -d --rm --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    oveits/jenkins:2.46.2-alpine-nologin-with-maven-git-pipelines`{{execute}}
    
You can load the Jenkins' dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ or by clicking the dashboard tab on the right.

#### Task: Create a Pipeline Workflow

1. On the **Jenkins** dashboard, select **create new jobs** under the Welcome message or **new Item* in the sidebar menue.
2. Give the job a friendly name such as **Pipeline Hello World**, select **Pipeline** and press **OK**.
3. On the upper right corner of the Pipeline Script Textbox, find the drop-down menue **try sample pipeline...** and choose **GitHub + Maven**
4. Review the Groovy code. You will see that we will use git for cloning a sample project and we will build the project using the Maven installation we had named "M3".
5. Click **Save**
6. Click **Build Now** in the side menue on the left.
7. Repeat step 6 several times. Some of the builds will be shown in green (stable), some will be shown in yellow (unstable). This comes from the fact, that the sample project we have chosen randomly throws errors, so we will get a nice Test Trend graph.
8. In the Browser, reload the page or press F5. Now a Test Result Trend will be shown:

Inline-style: 
![Jenkins Pipeline Dashboard with Test Result Trend](https://oliverveits.files.wordpress.com/2017/05/2017-05-12-10_53_17-pipeline-hello-world-jenkins.png "Jenkins Pipeline Dashboard with Test Result Trend")
