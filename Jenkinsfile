pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Tools') {
            steps {
                sh 'python3 --version'
                sh 'docker --version'
            }
        }

        stage('Install Dependencies and Test') {
            steps {
                sh 'python3 -m venv .venv'
                sh '.venv/bin/pip install -r requirements.txt pytest'
                sh '.venv/bin/python -m pytest tests/ -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-academic-platform:v1.0.0 .'
            }
        }
    }
}