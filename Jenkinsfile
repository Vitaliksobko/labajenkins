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
                sh 'docker build -t vitalkanyashka/jenkins_images .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_USR | docker login -u $DOCKERHUB_CREDENTIALS_PSW --password-stdin'
            }
        }
        stage('Push'){
            steps{
                sh 'docker push vitalkanyashka/jenkins_images'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
  
