pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('pre-build') {
            steps {
                sh 'rm trufflehog || true'
                sh 'docker run gesellix/trufflehog --json https://github.com/tuanklnew/BenchmarkJava.git > trufflehog'
                sh 'cat trufflehog'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
