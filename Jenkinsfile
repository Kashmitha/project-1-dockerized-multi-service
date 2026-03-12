pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build Images') {
            steps {
                echo '🐳 Building Docker images...'
                sh 'docker compose build'
            }
        }

        stage('Test Backend') {
            steps {
                echo 'Testing backend health...'
                sh '''
                    docker compose up -d backend
                    sleep 10
                    curl -f http://devops-backend:5000/health || exit 1
                    echo "Backend health check passed"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying services...'
                sh 'docker compose up -d'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo 'Verifying deployment...'
                sh '''
                    sleep 3
                    curl -f http://devops-backend:5000/ || exit 1
                    echo "✅ Deployment verified successfully"
                '''
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check logs above.'
            sh 'docker compose down || true'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
