pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker_hub_lee')
    }
    stages {
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/leenadharmik/nodejs-demo'
            }
        }

        stage('Build docker image') {
            steps {
                sh 'docker build -t leenadharmik/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push leenadharmik/nodeapp:$BUILD_NUMBER'
            }
        }
    }
}
