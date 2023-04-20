pipeline {
    agent any
    stages {
        stage('Docker version') {
            steps {
                sh '''
                    echo $USER
                    docker version
                '''
            }
        }
        stage('Checkout') {
            steps{
                git branch: 'main',
                    url: 'https://github.com/Vitaliksobko/labajenkins.git'        
                }
        }
        stage('Build docker image') {
            steps {
                sh '''
                    docker build -t vitalikanyashka/jenkins_images .
                '''
            }
            
        }
        
        stage('Push docker image to DockerHub') {
            steps {
                withDockerRegistry(credentialsId: 'Dockerhub', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push vitalikanyashka/jenkins_images
                    '''
                }
            }
        }
    }
}
