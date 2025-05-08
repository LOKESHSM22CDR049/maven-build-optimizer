pipeline {
    agent any
    tools {
        maven 'Maven 3.8.8'  // This should match the Maven name you configured
    }
    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code from Git...'
                checkout scm
            }
        }
        stage('Build with Parallel Execution') {
            steps {
                echo 'Starting Maven Parallel Build...'
                sh 'mvn -T 1C clean install'  // This will run the build with parallel execution
                echo 'Maven Build Completed.'
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
