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
                sh 'npm test'
            }
        }
        stage('Deliver') {
            steps {
                sh 'npm run build'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'npm start &'
            }
        }
    }
}
