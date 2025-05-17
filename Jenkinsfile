
  peline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = 'dockerhub-credentials-id' // Jenkins credentials ID
        DOCKER_HUB_USERNAME = 'your-dockerhub-username'
        BACKEND_IMAGE_NAME = 'devops-backend'
        FRONTEND_IMAGE_NAME = 'devops-frontend'
    }

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/HichemBenMosbah/devops.git'
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                dir('backend') {
                    script {
                        dockerImageBackend = docker.build("${DOCKER_HUB_USERNAME}/${BACKEND_IMAGE_NAME}")
                    }
                }
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('frontend') {
                    script {
                        dockerImageFrontend = docker.build("${DOCKER_HUB_USERNAME}/${FRONTEND_IMAGE_NAME}")
                    }
                }
            }
        }

        stage('Push Backend Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS) {
                        dockerImageBackend.push('latest')
                    }
                }
            }
        }

        stage('Push Frontend Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS) {
                        dockerImageFrontend.push('latest')
                    }
                }
            }
        }
    }
}
filebeat:
