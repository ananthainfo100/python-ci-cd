pipeline {
    agent any

    stages {

      
        stage('Setup Python') {
            steps {
                sh '''
                python3 -m venv venv
                ./venv/bin/pip install --upgrade pip
                ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                ./venv/bin/pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                mkdir -p /opt/python-app
                cp app.py /opt/python-app/
                '''
            }
        }
    }
}
