 def remote = [:]
    remote.name = 'ubuntu-A'
    remote.host = '192.168.81.182'
    remote.user = 'wangxing'
    remote.password = 'chengyue1212'
    remote.allowAnyHosts = true

 def remote_sec = [:]
    remote.name = 'ubuntu-B'
    remote.host = '192.168.81.129'
    remote.user = 'root'
    remote.password = '123456'
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
      parallel {
        stage('Upload-A') {
          steps {
            sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true, remote: remote)
          }
        }
        stage('ubuntu-B') {
          steps {
            sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', remote: '${remote_sec}', failOnError: true)
          }
        }
      }
    }
  }
}
