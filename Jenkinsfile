pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "alokik7/myapp"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Alokik07/my-devops-project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag myapp $DOCKER_IMAGE'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker rm -f myapp-container || true'
                sh 'docker run -d -p 5000:5000 --name myapp-container $DOCKER_IMAGE'
            }
        }
    }
}