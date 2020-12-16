// https://github.com/camunda/jenkins-global-shared-library
// https://github.com/camunda/cambpm-jenkins-shared-library
@Library(['camunda-ci', 'cambpm-jenkins-shared-library']) _

def failedStageTypes = []

pipeline {
  agent none
  options {
    buildDiscarder(logRotator(numToKeepStr: '5')) //, artifactNumToKeepStr: '30'
    copyArtifactPermission('*');
  }
  stages {
    stage('UNIT DB tests') {
      steps {
        script {
          parallel(cambpmGetMatrixStages('db-unit', failedStageTypes, 'cockroachdb'))
        }
      }
    }
  }
}