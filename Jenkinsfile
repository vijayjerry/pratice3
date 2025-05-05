pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-image'
        CONTAINER_NAME = 'my-container'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/vijayjerry/pratice3.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(IMAGE_NAME)
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop and remove old container if it exists
                    sh "docker rm -f ${CONTAINER_NAME} || true"

                    // Run new container
                    sh "docker run -d -p 5000:5000 --name ${CONTAINER_NAME} ${IMAGE_NAME}"
                }
            }
        }
    }
}

