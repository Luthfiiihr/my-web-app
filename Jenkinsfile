pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Luthfiiihr/my-web-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Stage') {
            steps {
                sh 'echo "No build needed for Node.js simple app"'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Starting deployment..."
                    pm2 restart my-web-app || pm2 start src/index.js --name my-web-app
                '''
            }
        }
    }

    post {
        always {
            echo "Pipeline Finish"
        }
    }
}
