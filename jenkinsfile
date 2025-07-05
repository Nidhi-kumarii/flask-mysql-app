pipeline {
    agent any

    environment {
        IMAGE_NAME = 'nidhikumari1/two-tier-flask-app'
        TAG = 'latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Nidhi-kumarii/flask-mysql-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:$TAG .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME:$TAG'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker rmi $IMAGE_NAME:$TAG || true'
            }
        }
    }
}

