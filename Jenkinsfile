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
        sshCommand()
        sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true)
      }
    }
  }
}