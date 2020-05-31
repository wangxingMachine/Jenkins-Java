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
BUILD_ID=dontKillMe nohup java -jar /home/newdisk/data/jenkins/workspace/Capistrano-java_master/target/cap-java.jar &
sleep 20
echo $(ps -ef|grep java)
echo "deploy script end"'''
      }
    }
  }
}
