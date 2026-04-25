pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/r4d1c4l3DDy/pipeline-jenkins1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest'
            }
        }
    }
}