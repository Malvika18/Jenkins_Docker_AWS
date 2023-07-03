pipeline {
    environment {
        registry = 'bhargava18/Flip-Book'
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning our Git') {
            steps {
                git 'https://github.com/Malvika18/Flip-Book.git'
            }
        }
        stage('Building our image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Deploy our image') {
            steps {
                script {
                    docker.withRegistry('', registryCredential) {
                        dockerImage.push()
                    }
                }
            }
        }
        stage('Cleaning up') {
            steps {
                sh "docker rmi $registry:$BUILD_NUMBER"
            }
        }
    }
}



///Task to get the Dockerfile from the git repo create an image of it and push the image to the aws insatnce.


pipeline {
    environment {
        registry = 'bhargava18/Flip-Book'
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning our Git') {
            steps {
                git 'https://github.com/Malvika18/Flip-Book.git'
            }
        }
        stage('Building our image') {
            steps {
                script {
                    sh "docker build . -t my-website:latest"
                    sh "docker images"
                    sh "docker run -d -p 80:80 my-website:latest"
                }
            }
        }
        
        
        
    }
}
