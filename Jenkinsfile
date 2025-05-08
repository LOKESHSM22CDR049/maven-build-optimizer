pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8'  // Make sure this matches the Maven installation name in Jenkins
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
                sh 'time mvn -T 1C clean install'
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
