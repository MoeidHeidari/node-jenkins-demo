podTemplate(
    // create a custom pod with nodejs container
    yaml: """
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
) {
    node(POD_LABEL) {
        // We can use multiple stages for different steps of the pipeline
        stage('Checkout') {
            checkout scm
        }

        stage('Install Dependencies') {
            container('nodejs') {
                sh 'npm install'
            }
        }

        stage('Test') {
            container('nodejs') {
                sh 'npm test'
            }
        }

        stage('Build') {
            container('nodejs') {
                sh 'npm run build'
            }
        }
    }
}
