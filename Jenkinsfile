pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Upload') {
      def remote = [:]
    remote.name = 'ubuntu'
    remote.host = '192.168.81.182'
    remote.user = 'root'
    remote.password = 'chengyue1212'
    remote.allowAnyHosts = true
      steps {
        sshPut(from: 'target/cap-java.jar', into: '/home/wangxing/java/jenkins', failOnError: true, remote: remote)
      }
    }
  }
}
