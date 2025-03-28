pipeline {
    agent any

    environment {
        IMAGE_NAME = "subashthiruppathy/react-app"
        CONTAINER_NAME = "react-app-container"
        DOCKER_HUB_USER = "subashthiruppathy@gmail.com"
        DOCKER_HUB_PASS = "xybnak-kivgyj-2fuJqy"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/subash-thiruppathi/react.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME}:latest ."
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh "echo ${DOCKER_HUB_PASS} | docker login -u ${DOCKER_HUB_USER} --password-stdin"
                    sh "docker push ${IMAGE_NAME}:latest"
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    sh "docker stop ${CONTAINER_NAME} || true"
                    sh "docker rm ${CONTAINER_NAME} || true"
                    sh "docker run -d --name ${CONTAINER_NAME} -p 3000:3000 ${IMAGE_NAME}:latest"
                }
            }
        }
    }
}
