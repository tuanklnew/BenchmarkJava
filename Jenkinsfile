pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('pre-build') {
            parallel{
                stage('depedency-check') {
                    steps {
                        echo "Depedency-check"
                    }
                }
                stage('secret-check') {
                    steps {
                        sh 'rm trufflehog || true'
                        sh 'docker run gesellix/trufflehog --json https://github.com/tuanklnew/BenchmarkJava.git |& tee trufflehog'
                        sh 'cat trufflehog'
                    }
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
