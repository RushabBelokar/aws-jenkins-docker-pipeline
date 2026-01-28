pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t my-website:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop web-container || true'
                sh 'docker rm web-container || true'
                sh 'docker run -d --name web-container -p 80:80 my-website:latest'
            }
        }
    }
}