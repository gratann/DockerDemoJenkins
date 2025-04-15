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
                // This happens automatically when using Pipeline from SCM
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "🐳 Building image..."
                bat "docker build -t %IMAGE_NAME%:%IMAGE_TAG% ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "🚀 Running container..."
                bat "docker run -d --rm -p 8080:80 --name demo_container %IMAGE_NAME%:%IMAGE_TAG%"
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
