pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test Flask Application') {
            steps {
                sh 'python --version'
                sh 'python -m pip install -r requirements.txt'
                sh 'python -m pip install pytest'
                sh 'python -m pytest tests/ -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-academic-platform:v1.0.0 .'
            }
        }
    }
}
