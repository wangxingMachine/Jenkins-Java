pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Deploy') {
      steps {
        sh 'nohup java -jar target/cap-java.jar &'
      }
    }
  }
}