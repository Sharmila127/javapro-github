pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'maven3'
    }

    environment {
        DOCKERHUB_USER = credentials('dockerhub-username')
        DOCKERHUB_PASS = credentials('dockerhub-password')
        IMAGE_NAME = "${DOCKERHUB_USER}/java-docker-app:latest"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sharmila127/javapro-github.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn -B package'
            }
        }

        stage('Docker Login') {
            steps {
                sh """
                echo "${DOCKERHUB_PASS}" | docker login -u "${DOCKERHUB_USER}" --password-stdin
                """
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push ${IMAGE_NAME}'
            }
        }

        stage('Deploy on Local Ubuntu') {
            steps {
                sh """
                docker rm -f javaapp || true
                docker pull ${IMAGE_NAME}
                docker run -d -p 8090:8080 --name javaapp ${IMAGE_NAME}
                docker ps
                """
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully on local Ubuntu'
        }
        failure {
            echo 'Deployment failed'
        }
    }
}
