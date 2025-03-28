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
            emailext subject: "Jenkins Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                     body: "Good news! The build ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.\nCheck: ${env.BUILD_URL}",
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
        failure {
            emailext subject: "Jenkins Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                     body: "Oops! The build ${env.JOB_NAME} #${env.BUILD_NUMBER} failed.\nCheck logs: ${env.BUILD_URL}",
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
    }
}
