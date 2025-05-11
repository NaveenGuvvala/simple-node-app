pipeline {
    agent any

    environment {
        IMAGE_NAME = 'naveenguvvala/simple-node-app'
        DOCKER_CREDENTIALS_ID = 'dockerhub-creds'
    }

    stages {
        stage('Clone Code') {
            steps {
                git url: 'https://github.com/NaveenGuvvala/simple-node-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        docker.image("${IMAGE_NAME}").push()
                    }
                }
            }
        }
    }
}
