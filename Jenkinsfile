pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker_hub') // Replace with your Docker Hub credentials ID in Jenkins
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/jaiymzN/helloDocker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t sairohit1998/hello-docker:${BUILD_NUMBER} .
                '''
            }
        }
        stage('Push Docker Image') {
            steps {
                sh '''
                echo $DOCKER_HUB_CREDENTIALS_PSW | docker login -u $DOCKER_HUB_CREDENTIALS_USR --password-stdin
                docker push sairohit1998/hello-docker:${BUILD_NUMBER}
                '''
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl --kubeconfig=C:/Program Files/Jenkins/config.yml apply -f deploymentsvc.yaml
                '''
            }
        }
    }
}
