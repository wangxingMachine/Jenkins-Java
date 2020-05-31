def remote = [:]
    remote.name = 'ubuntu-java'
    remote.host = '192.168.81.182'
    remote.user = 'root'
    remote.password = 'chengyue1212'
    remote.allowAnyHosts = true

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Upload') {
      steps {
        sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true, remote: remote)
      }
    }
  }
}
