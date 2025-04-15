pipeline {
    agent any

    environment {
        IMAGE_NAME = "demoapp"
        IMAGE_TAG = "v1"
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo "📥 Cloning repo..."
                checkout scm  // Automatically clones the repository
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "🐳 Building image..."
                bat "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "🚀 Running container..."
                bat "docker run -d --rm -p 8081:80 --name demo_container ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }
    }

    post {
        success {
            echo "✅ Deployment succeeded."
        }
        failure {
            echo "❌ Build failed."
        }
    }
}
