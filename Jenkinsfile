pipeline {
    agent any // Run the overall pipeline controller on any available agent

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // This stage runs on the base Jenkins agent
            }
        }
        stage('Test') {
            agent {
                docker { image 'python:3.9-slim' }
            }
            steps {
                echo 'Testing inside a Python container...'
                sh 'python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt && pytest'
            }
        }
    }
}