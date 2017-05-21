In this scenario you'll dog into an increasingly popular Jenkins plugin named [Pipeline](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Plugin). It uses Groovy scripts to define Jenkins workflows as code.

#### Why is Pipeline so popular?  

The pupularity of the Pipeline plugin can be observed in its usage chart:
<!-- [Pipeline Popularity 2016/2017](https://oliverveits.files.wordpress.com/2017/05/2017-05-20-23_38_04-pipeline-plugin-jenkins-jenkins-wiki.png)  -->
![Pipeline Popularity](https://chart.googleapis.com/chart?cht=lc&chxl=1:%7C05%7C06%7C07%7C08%7C09%7C10%7C11%7C12%7C01%7C02%7C03%7C04%7C2:%7CMonth&chxp=2,50&chxr=0,0,78094%7C1,0,12&chxs=1,676767,12&chxt=y,x,x&chs=300x225&chds=0,78094&chd=t:24577,28597,34295,41499,46817,50825,56172,58495,67387,68753,77674,78094&chg=9.09,-1,0,0&chls=4&chco=d24939&chtt=workflow-aggregator+-+installations)

Pipelines offer the following possibilities (see also [here](https://jenkins.io/doc/book/pipeline/#why)):
- **Code**: Pipeline users can put workflows under source control (e.g. git), so they can add edit, review and 
- **Durable**: a Task that is interupted by a planned or unplanned restart of the server is handled gracefully by the [Durable Task Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Durable+Task+Plugin) included in the [Pipeline Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Plugin)
- **Interactive/Pausable**: manual steps can be added to pipeline workflows
- **Versatile**: you can create complex workflows including workflow forks and joins
- **Extensible**: Pipeline users can create and add custom extension to the Pipeline domain specific language (DSL)

The scenario is designed to demostrate how you can use Groovy Pipelines within a Continuous Intagration/Delivery (CI/CD) workflow to download software code from [GitHub](https://github.com/), perform unit tests and display a historical test result report.

You will learn how to make use of a Docker host environment for running Jenkins in a Docker container. The steps guide you to installing the required plugins, creating and running a Software build process build and viewing the test report results.
