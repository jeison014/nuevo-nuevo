pipeline {
    agent any

    stages {
        stage('Docker version') {
            steps {
            
                sh 'docker version'
            }
        }
        
        stage('Checkout') {
            steps{
                git branch: 'main',
                    url: 'https://github.com/jeison014/docker-lessons.git'        
                }
        }
        stage('Test') {
            steps{
                dir('lesson-1') {
                    sh "ls -la "
                    sh "pwd"
                }
                    sh "ls -la "
                    sh "pwd"
            }
        }
        stage('Build docker image') {
            steps{
                dir('lesson-1') {
                    sh 'docker build -t jeison014/jenkins-images .'
                }
            
            }
           
        }
         stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'dockerhub-cred-jeison014', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push jeison014/jenkins-images
                    '''
                }
            }
        }
    }
}
