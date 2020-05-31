pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Upload-A') {
      steps {
        sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true, remote: remote=remote.name = 'ubuntu-A'   remote.host = '192.168.81.182'   remote.user = 'wangxing'   remote.password = 'chengyue1212'   remote.allowAnyHosts = true)
      }
    }
    stage('Restart') {
      steps {
        sshCommand(command: 'nohup /opt/jdk1.8.0_172/bin/java -jar /home/wangxing/java/jenkins/cap-java.jar &', failOnError: true, remote: remote=remote.name = 'ubuntu-A'   remote.host = '192.168.81.182'   remote.user = 'wangxing'   remote.password = 'chengyue1212'   remote.allowAnyHosts = true)
      }
    }
  }
}