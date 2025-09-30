pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/shodhan-simpleenergy/1st-Node_js-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-node-app:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image("my-node-app:${env.BUILD_NUMBER}").push()
                    }
                }
            }
        }
    }
}

