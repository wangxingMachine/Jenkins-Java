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
source ~/.bashrc

nohup java -jar target/cap-java.jar &
echo "deploy script end"'''
      }
    }
  }
}