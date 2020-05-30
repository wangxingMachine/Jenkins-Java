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
echo $(ps -ef|grep java)
sh ./deploy_java.sh
echo "deploy script end"'''
      }
    }
  }
}