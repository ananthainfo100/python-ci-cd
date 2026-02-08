pipeline {
    agent any

    environment {
        IMAGE_NAME = "python-ci-cd-app"
        IMAGE_TAG  = "${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ananthainfo100/python-ci-cd.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build --no-cache -t $IMAGE_NAME:$IMAGE_TAG .
                '''
            }
        }

        stage('Test Container') {
            steps {
                sh '''
                docker run --rm $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f python-app || true
                docker run -d --name python-app $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }
    }
}
