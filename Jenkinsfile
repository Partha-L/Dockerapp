pipeline {
    agent any

    stages {

        Stage('Checkout Code') {
            steps{
                git 'https://github.com/Partha-L/Dockerapp.git'
            }

        }

        stage('Build Docker Image'){
            steps{
                sh 'docker build -t flask-cicd-app .'
            }
        }

        stage('Stop Old Container'){
            
            steps{

                  sh '''

                  docker stop flask_container || true
                  docker rm flask_container || true

                  '''
        
            }
        }

        stage ('Run New Container')
        {
            steps{

                sh '''

                docker run -d -p 5000:5000 \

                --name flask_container  flask-cicd-app

                '''
            }
        }

    }
}