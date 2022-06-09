pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Hello') {
            steps {
                sshagent(['docker']) {
                    sh 'ssh -o  StrictHostKeyChecking=no ubuntu@192.168.74.133 "ifconfig"'
                }
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
