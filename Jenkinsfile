pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3003:3003'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'bash ./jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh 'bash ./jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'bash ./jenkins/scripts/kill.sh'
            }
        }
    }
}
