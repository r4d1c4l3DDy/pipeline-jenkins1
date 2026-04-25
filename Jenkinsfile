pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                python -m pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                python -m pytest
                '''
            }
        }
    }
}