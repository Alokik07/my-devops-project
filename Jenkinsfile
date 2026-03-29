pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Alokik07/my-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop myapp-container || true'
                sh 'docker rm myapp-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name myapp-container myapp'
            }
        }
    }
}