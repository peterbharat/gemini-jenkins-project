pipeline {
    // 1. Tell Jenkins to NOT use the main server for any work.
    agent none

    stages {
        stage('Build and Test') {
            // 2. Define a single, clean environment for ALL work.
            //    We use an official Python image that is Debian-based.
            agent {
                docker { image 'python:3.9-bullseye' }
            }
            steps {
                // 3. Inside the clean container, install the tools we need.
                echo 'Installing Git...'
                sh 'apt-get update && apt-get install -y git'

                // 4. NOW it's safe to check out the code.
                echo 'Checking out code...'
                checkout scm

                // 5. Finally, run the tests as before.
                echo 'Installing dependencies and running tests...'
                sh 'python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt && pytest'
            }
        }
    }
}