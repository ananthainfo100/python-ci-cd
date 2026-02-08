pipeline {
    agent any

    stages {

      
        stage('Setup Python') {
            steps {
                sh '''
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                source venv/bin/activate
                pytest
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
