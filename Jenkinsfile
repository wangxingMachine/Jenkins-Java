pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Upload') {
      parallel {
        stage('Upload-A') {
          steps {
            sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true, remote: remote)
          }
        }
        stage('ubuntu-B') {
          steps {
            sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', remote: '${remote_sec}', failOnError: true)
          }
        }
      }
    }
  }
}