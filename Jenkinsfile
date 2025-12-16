pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "yourdockerhubusername/devops-ci-cd-project"
    }

    stages {

        stage('Code Fetch Stage') {
            steps {
                git branch: 'main',
                url: 'https://github.com/AKTechWiz/devops-ci-cd-project.git'
            }
        }

        stage('Docker Image Build') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:latest")
                }
            }
        }

        stage('Docker Image Push') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-creds') {
                        docker.image("${DOCKER_IMAGE}:latest").push()
                    }
                }
            }
        }
    }
}
