pipeline {
    agent any

    environment {
        IMAGE_NAME = "arya08/git:3.11"
        IMAGE_TAG  = "3.11"
    }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t git:3.11:3.11 .'
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'arya08',
                    passwordVariable: 'AaZz@@1234'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }
         stage('Push Image') {
            steps {
                sh 'docker push git:3.11'
            }
        }
    }
