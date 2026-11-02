

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
                echo 'Building application'
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Running application tests'

                sh 'test -f index.html'
                sh 'grep -q "wrong text" index.html'

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

                echo 'Deployment completed!'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Pipeline completed!'
        }

        failure {
            echo 'FAILURE: Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}

          
