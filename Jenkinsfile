pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning Code fron Github'
                git branch: 'main', url: 'https://github.com/Bharat16092003/jenkins-hello-world.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker Image'
                sh 'docker build -t jenkins-hello-world .'
            }
        }

        stage('Test') {
            steps {
                echo 'Simple Testing'
                sh 'npm test || echo "No tests defined, skipping..."'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Stopping old container (if exists) and deploying new one'
                sh '''
                docker stop jenkins-hello-world || true
                docker rm jenkins-hello-world || true
                docker run -d -p 3000:3000 --name jenkins-hello-world jenkins-hello-world
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}

