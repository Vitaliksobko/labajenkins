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
        
        stage('Build docker image') {
            steps {
                sh '''
                    docker build -t vitalikanyashka/jenkins_images .
                '''
            }
            
        }
        
        
        stage('Push docker image to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'new_id', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        docker push vitalikanyashka/jenkins_images
                    '''
                }
            }
        }
    }
}
