pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'python3 --version || true'
                sh 'pip3 install --user -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh '~/.local/bin/pytest'
            }
        }
    }
}