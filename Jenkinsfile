pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "subashthiruppathy/myapp:latest"  // Change to your repo
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/subash-thiruppathi/react.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                docker run -d --name myapp -p 3000:3000 $DOCKER_IMAGE
                '''
            }
        }
    }
    post {
        success {
            emailext subject: "Jenkins Build Successful",
                     body: "The build and deployment were successful!",
                     to: "subashthiruppathy@gmail.com"
        }
        failure {
            emailext subject: "Jenkins Build Failed",
                     body: "Something went wrong!",
                     to: "subashthiruppathy@gmail.com"
        }
    }
}
