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
echo "start kill cap-java"
pid=`ps -ef|grep cap-java|awk '{print $2}'`
kill -9 $pid
echo "kill $pid success"
OLD_BUILD_ID=$BUILD_ID
echo $OLD_BUILD_ID
BUILD_ID=DONTKILLME nohup java -jar /home/newdisk/data/jenkins/workspace/Capistrano-java_master/target/cap-java.jar &
sleep 30
echo $(ps -ef|grep java)
echo "deploy script end"'''
      }
    }
  }
}
