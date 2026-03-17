pipeline {
    agent any

    environment {
        DOCKER_IMAGE = '2023bcs0166'
        DOCKER_HUB_USER = 'tejasri06'
        DOCKER_CREDS_ID = 'dockerhub-credentials'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tejasri06/2023bcs0166 .'
            }
        }

        stage('Login DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push tejasri06/2023bcs0166'
            }
        }
    }
}