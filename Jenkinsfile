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
                  sh "ls"
                  sh " docker image build -t  springboot:${env.GIT_COMMIT} ."
              }
         }
         stage('Deploy Docker Image') {
            steps {
                sh 'docker run -d -p 2000:8080 springboot:${env.GIT_COMMIT}'
            }
        }



    }

    post {
        always {
            cleanWs()
        }
    }
}