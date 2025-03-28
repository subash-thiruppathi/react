pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sleep 2
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sleep 2
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment successful!'
            }
        }
    }
        post {
            success {
                emailext to: 'subashthiruppathy@gmail.com',
                         subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.\nCheck logs: ${env.BUILD_URL}"
            }
            failure {
                emailext to: 'subashthiruppathy@gmail.com',
                         subject: "Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} failed.\nCheck logs: ${env.BUILD_URL}"
            }
        }
}
