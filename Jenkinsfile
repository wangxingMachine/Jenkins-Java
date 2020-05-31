 def remote = [:]
    remote.name = 'ubuntu-A'
    remote.host = '192.168.81.182'
    remote.user = 'wangxing'
    remote.password = 'chengyue1212'
    remote.allowAnyHosts = true

 def remote_sec = [:]
    remote_sec.name = 'ubuntu-B'
    remote_sec.host = '192.168.81.129'
    remote_sec.user = 'root'
    remote_sec.password = '123456'
    remote_sec.allowAnyHosts = true
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
  }
}
