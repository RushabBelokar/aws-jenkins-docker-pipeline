pipeline {
    agent any
    
    // Define variables here so you only change them in one place
    environment {
        REPO_URL = 'https://github.com/RushabBelokar/aws-jenkins-docker-pipeline.git'
        DOCKER_IMAGE = "rushabbelokar/docker-web-app:${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                // 'checkout scm' automatically uses the repo that triggered the build
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                // Ensure your Dockerfile is in the root of your repo
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }

        stage('Deploy') {
            steps {
                // This stops any old version and runs the new one
                sh "docker stop my-web-container || true"
                sh "docker rm my-web-container || true"
                sh "docker run -d --name my-web-container -p 80:80 ${DOCKER_IMAGE}"
            }
        }
    }
}
