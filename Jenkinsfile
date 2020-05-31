pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Upload') {
      steps {
        sshPublisher(alwaysPublishFromMaster: true, failOnError: true, masterNodeName: 'master')
      }
    }
  }
}