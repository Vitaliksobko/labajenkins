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
                    docker build -t vitalkanyashka/jenkins_images .
                '''
            }
            
        }
        stage('docker login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'Docker', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])  {
            sh"""
            docker login -u $USERNAME -p $PASSWORD
            """
                }
            }
        }
        
        stage('Push docker image to DockerHub') {
            steps {
                    sh '''
                        docker push vitalkanyashka/jenkins_images
                    '''
                    
                }
            }
        }
}
