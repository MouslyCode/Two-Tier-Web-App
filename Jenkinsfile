pipeline{
    agent any

    stages{
        stage("Clone Code"){
            steps{
                git branch: 'main', url: 'https://github.com/MouslyCode/Two-Tier-Web-App.git'
            }
        }
        stage("Build Docker Image"){
            steps{
                sh 'docker build -t flask-app:latest .'
            }
        }
        stage("Deploy with Docker Compose"){
            steps{
                // Stop existiing containers
                sh 'docker compose down || true'
                // Starting the aplication, and rebuilding the flask image
                sh 'docker compose up -d --build'
            }
        }
    }
}