ipeline {
    agent {
        kubernetes {
            // Defining pod and container templates
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: nodejs
    image: node:14
    command:
    - cat
    tty: true
"""
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
                container('nodejs') {
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                container('nodejs') {
                    sh 'npm test'
                }
            }
        }
        stage('Build') {
            steps {
                container('nodejs') {
                    sh 'npm run build'
                }
            }
        }
    }
}
