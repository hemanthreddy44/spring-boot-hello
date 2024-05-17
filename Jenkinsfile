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

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://my-docker-registry.com', 'my-docker-credentials-id') {
                        docker.image("my-docker-image").push("my-tag")
                    }
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