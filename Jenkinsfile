pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // In a real project, this is where you might compile code
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt && pytest'
            }
        }
    }
}