pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/USERNAME/nextjs-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-nextjs-app .'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker tag my-nextjs-app USERNAME/my-nextjs-app:latest'
                sh 'docker push USERNAME/my-nextjs-app:latest'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:3000 --name nextjs-container USERNAME/my-nextjs-app:latest'
            }
        }
    }
}

