
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application'
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application'
                sh 'test -f index.html'
                sh 'grep -q "Hello Jenkins" index.html'
                echo 'All tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
                sh '''
                    mkdir -p deploy-demo
                    cp index.html deploy-demo/
                '''
                echo 'Demo deployment completed'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
