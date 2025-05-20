pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8'  // This must match the Maven tool name configured in Jenkins
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo '📥 Checking out code from Git...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '🔧 Running mvn clean compile...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running mvn test...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '📦 Running mvn package...'
                sh 'mvn package'
            }
        }

        stage('Build with Parallel Execution') {
            steps {
                echo '🚀 Starting Maven Parallel Build...'
                sh 'mvn -T 1C clean install'
                echo '✅ Maven Build Completed.'
            }
        }
    }

    post {
        success {
            echo '✅ Build finished successfully!'
        }
        failure {
            echo '❌ Build failed.'
        }
    }
}

