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
source /etc/profile

nohup java -jar target/cap-java.jar &
echo "deploy script end"'''
      }
    }
  }
}