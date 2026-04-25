pipeline {
    agent {
        docker {
            image 'python:3.11'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                python -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }
    }
}