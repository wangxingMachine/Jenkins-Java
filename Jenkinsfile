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
        sh '''echo "start deploy script"

BUILD_ID=DONTKILLME
nohup java -jar target/cap-java.jar &
echo "deploy script end"'''
      }
    }
  }
}