pipeline {
    agent any

    environment {
        IMAGE_NAME = "mywebsite:latest"
        CONTAINER_NAME = "website_container"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Muraliruttala/krishn.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop $CONTAINER_NAME || true'
                sh 'docker rm $CONTAINER_NAME || true'
                sh 'docker run -d -p 80:80 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
