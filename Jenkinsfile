pipeline {
    agent {
        docker {
            image 'python:3.11'
        }
    }

    stages {
        stage('Test (CI)') {
            steps {
                sh '''
                python --version
                pip install --upgrade pip
                pip install -r requirements.txt
                pytest
                '''
            }
        }

        stage('Approval') {
            steps {
                input message: 'Testes OK. Fazer merge na main?'
            }
        }

        stage('Merge') {
            steps {
                sh '''
                git config user.email "jenkins@local"
                git config user.name "jenkins"

                git fetch origin
                git checkout main
                git pull origin main

                git merge sem-docker -m "merge aprovado pelo Jenkins"

                git push origin main
                '''
            }
        }
    }
}