pipeline {
    agent any

    stages {
        stage('Clean') {
            steps {
                sh 'rm -rf venv'
            }
        }

        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                venv/bin/python -m pip install -r requirements.txt

                echo "=== DEBUG ==="
                venv/bin/python --version
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'venv/bin/python -m pytest'
            }
        }
    }
}