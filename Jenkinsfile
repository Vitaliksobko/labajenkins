pipeline {
    agent any
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
        stage('Build docker image') {
            steps {
                sh '''
                    docker build -t vitalkanyashka/jenkins_images .
                '''
            }
        }
        stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'Docker_jenkins', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push vitalkanyashka/jenkins_images
                    '''
                }
            }
        }
    }
