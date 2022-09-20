pipeline {
    agent any

    stages {
        stage('Docker version') {
            steps {
            
                shell 'docker version'
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
                    shell "ls -la "
                    shell "pwd"
                }
                    shell "ls -la "
                    shell "pwd"
            }
        }
        stage('Build docker image') {
            steps{
                dir('lesson-1') {
                    shell 'docker build -t jeison014/jenkins-images .'
                }
            
            }
           
        }
         stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'dockerhub-cred-jeison014', url: 'https://index.docker.io/v1/') {
                    shell '''
                        docker push jeison014/jenkins-images
                    '''
                }
            }
        }
    }
}
