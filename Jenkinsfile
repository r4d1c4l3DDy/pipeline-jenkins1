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
                pip install -r requirements.txt
                pytest
                '''
            }
        }

        stage('Approval') {
            steps {
                input message: 'Testes passaram. Deseja fazer merge na main?'
            }
        }

        stage('Prepare Merge') {
            steps {
                sh '''
                git config user.email "jenkins@local"
                git config user.name "jenkins"

                git fetch origin
                git checkout com-docker

                # opcional: remover Jenkinsfile antes do merge
                #rm -f Jenkinsfile
                #git add .
                #git commit -m "remove Jenkinsfile before merge" || true

                git checkout main
                git pull origin main

                git merge com-docker --no-ff -m "merge automático após aprovação Jenkins"

                git push origin main
                '''
            }
        }
    }
}