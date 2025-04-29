pipeline {
agent any

environment {
    GITHUB_TOKEN = credentials('github-token')
}

stages {
    stage('Checkout') {
        steps {
            git url: 'https://github.com/AnkitKumarSingh22/Real-estate', credentialsId: 'github-token'
        }
    }

    stage('Build Docker Image') {
        steps {
            script {
                sh 'docker build -t real-state-app .'
            }
        }
    }

    stage('Run Docker Image') {
        steps {
            script {
                sh 'docker run -d -p 8085:8080 real-state-app'
            }
        }
    }
}

post {
    success {
        echo 'Build and deployment succeeded!'
    }
    failure {
        echo 'Build or deployment failed!'
    }
}
}