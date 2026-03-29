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

        stage('Tag Image') {
            steps {
                sh 'docker tag myapp yourusername/myapp'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push yourusername/myapp'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker rm -f myapp-container || true'
                sh 'docker run -d -p 5000:5000 --name myapp-container yourusername/myapp'
            }
        }
    }
}