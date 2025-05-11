pipeline {
    agent any

    environment {
        IMAGE_NAME = 'guvvala5222/simple-node-app'
        DOCKER_CREDENTIALS_ID = 'N@veen5222#'
    }

    stages {
        stage('Clone Repo') {
            steps {
                https://github.com/NaveenGuvvala/simple-node-app.git
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
