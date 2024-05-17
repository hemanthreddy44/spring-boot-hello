pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-docker-image", "-f Dockerfile .")
                }
            }
        }


    }

    post {
        always {
            cleanWs()
        }
    }
}