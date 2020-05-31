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
            sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', remote: remote_sec, failOnError: true)
          }
        }
      }
    }
    stage('Restart') {
      steps {
        sshCommand(command: 'nohup java -jar /home/wangxing/java/jenkins/cap-java.jar &', failOnError: true, remote: '${remote}')
      }
    }
  }
}