pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7' // Adjust if using a different Maven installation name
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Check Directory') {
            steps {
                script {
                    echo "Listing contents of workspace:"
                    sh 'pwd'
                    sh 'ls -la'
                }
            }
        }

        stage('Parallel Build') {
            parallel {
                stage('Build Core') {
                    steps {
                        echo 'Building all modules (Core phase)...'
                        sh 'cd maven-build-project && mvn clean install -T 2'
                    }
                }
                stage('Build API') {
                    steps {
                        echo 'Building all modules (API phase)...'
                        sh 'cd maven-build-project && mvn clean install -T 2'
                    }
                }
                stage('Build Service') {
                    steps {
                        echo 'Building all modules (Service phase)...'
                        sh 'cd maven-build-project && mvn clean install -T 2'
                    }
                }
                stage('Build Web') {
                    steps {
                        echo 'Building all modules (Web phase)...'
                        sh 'cd maven-build-project && mvn clean install -T 2'
                    }
                }
            }
        }
    }
}
