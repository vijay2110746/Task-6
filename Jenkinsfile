pipeline {
    agent any

    environment {
        IMAGE_NAME = "nandhana/flask-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/vijay2110746/Task-6.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t %IMAGE_NAME% .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    bat 'docker run -d -p 5000:5000 --name flask-container %IMAGE_NAME%'
                }
            }
        }

        stage('Cleanup Previous Containers') {
            steps {
                script {
                    bat 'docker stop flask-container || echo No running container'
                    bat 'docker rm flask-container || echo No container to remove'
                    bat 'docker rmi %IMAGE_NAME% || echo No image to remove'
                }
            }
        }
    }
}
