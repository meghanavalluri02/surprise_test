pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/meghanavalluri02/surprise_test.git'
            }
        }
        stage('Setup') {
            steps {
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate'
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh 'source venv/bin/activate && pytest tests/'
            }
        }
        stage('Build') {
            steps {
                sh 'python setup.py bdist_wheel'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'dist/*.whl', fingerprint: true
            }
        }
    }
}
