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
sh deploy_java.sh
echo "deploy script end"'''
      }
    }
  }
}