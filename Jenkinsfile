pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker_hub') 
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Sairohit1998/helloDocker'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat '''
                kubectl --kubeconfig="C:/Program Files/Jenkins/config.yml" apply -f deploymentsvc.yaml
                '''
            }
        }
    }
}
