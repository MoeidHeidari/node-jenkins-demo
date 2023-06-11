pipeline {
    agent {
        docker {
            label 'docker-agent'
            image 'node:14-alpine' 
            args '-v /home/node/.npm:/home/node/.npm'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        
    }
}
