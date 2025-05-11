pipeline {
    agent any

    environment {
        IMAGE_NAME = 'yourdockerhubusername/simple-node-app'
        DOCKER_CREDENTIALS_ID = 'dockerhub-creds'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/yourusername/simple-node-app.git'
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
