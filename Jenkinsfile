pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                venv/bin/python -m pip install -r requirements.txt

                echo "=== DEBUG VENV ==="
                venv/bin/python --version
                venv/bin/pip --version
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                venv/bin/python -m pytest
                '''
            }
        }
    }
}