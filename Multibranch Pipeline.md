# Building a Multibranch Jenkins Pipeline

### The Scenario
Your team is building a train scheduling app. Continuous integration has already been implemented in Jenkins, but they want to move toward doing automated deployments as well. You have been asked to build a Jenkins Pipeline project called train-schedule to build the train-schedule app. The pipeline project needs to build the code, run the automated tests, and archive the deployable zip artifact that is created by the build.

## Solution

*  Fork repo https://github.com/linuxacademy/cicd-pipeline-train-schedule-pipelines

* Build the Master Branch of the train-schedule Pipeline Project

* Create a new Jenkinsfile with the content below:
```Jenkinsfile
pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        echo 'Running build automation'
        sh './gradlew build --no-daemon'
        archiveArtifacts artifacts: 'dist/trainSchedule.zip'
      }
    }
  }
}
```

* Generate Token from your GitHub settings

* Create New Item as  Multibranch Pipeline

* Under Branch Sources add Github repo URL with the credentials(the token generated before is the password).

* Click Save and Scan begins for Jenkinsfiles on each branches in the repo

* Once Scan completes(initial build might take few minutes longer) you will see branches that Jenkins found Jenkinsfile with Build Now availble as an option on the left.