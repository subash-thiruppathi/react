pipeline {
    agent any  // Runs on any available Jenkins agent

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/subash-thiruppathi/react.git'  // Replace with your repo
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building project..."'
                sh 'sleep 2'  // Simulate build process
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'sleep 2'  // Simulate test process
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deployment successful!"'
            }
        }
    }
}
