pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('Docker_push')
    }
    stages {
        stage('Docker version') {
            steps {
                sh '''
                    echo $USER
                    docker version
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t vitalikanyashka/jenkins_images .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push'){
            steps{
                sh 'docker push vitalikanyashka/jenkins_images'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
  
