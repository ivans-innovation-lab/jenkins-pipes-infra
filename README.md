
# Infrastructure - Jenkins And Artifactory

Jenkins 2.x with the [Pipeline Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Plugin) and Artifactory docker images to support the following scenario:

 * all jobs are under version control and described via [Job-DSL](https://github.com/jenkinsci/job-dsl-plugin/wiki), see the [my-company-ci-jobs](https://github.com/ivans-innovation-lab/my-company-ci-jobs) repo
 * there is a [seed-job](https://github.com/ivans-innovation-lab/my-company-infrastructure/blob/master/seedJob.xml) which runs periodically to ensure the aforementioned jobs exist in Jenkins
 * each project to be built by these jobs defines its own pipeline via [Pipeline-DSL](https://jenkins.io/doc/book/pipeline/syntax/) in a `Jenkinsfile`, see the:

  - [my-company-monolith](https://github.com/ivans-innovation-lab/my-company-monolith)
  - [my-company-common](https://github.com/ivans-innovation-lab/my-company-common)
  - [my-company-blog-domain](https://github.com/ivans-innovation-lab/my-company-blog-domain)
  - [my-company-project-domain](https://github.com/ivans-innovation-lab/my-company-project-domain)
  - [my-company-blog-materialized-view](https://github.com/ivans-innovation-lab/my-company-blog-materialized-view)
  - [my-company-project-materialized-view](https://github.com/ivans-innovation-lab/my-company-project-materialized-view)
  
* artifacts are deployed on Artifactory instance. Parrent maven [pom](https://github.com/ivans-innovation-lab/my-company-common/blob/master/pom.xml) file is configured to use the Artifactory.


## Running instructions

```
$ ./start.sh gituser gitpassword
```

Once Jenkins is started you should see at least the seed-job on [http://localhost:9090](http://localhost:9090).

If it has not run yet, simply trigger it and see how the actual jobs get created.

Artifactory is available on [http://localhost:9091](http://localhost:9091)


## References and further reading

-  [Maven Release Plugin and Jenkins Pipeline](https://www.cloudbees.com/blog/new-way-do-continuous-delivery-maven-and-jenkins-pipeline)
- [Declarative Pipeline: Notifications and Shared Libraries](https://jenkins.io/blog/2017/02/15/declarative-notifications)
