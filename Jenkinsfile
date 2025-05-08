pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code from Git repository...'
                git url: 'https://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@github.com/LOKESHSM22CDR049/maven-build-optimizer.git', branch: 'main'
            }
        }

        stage('Parallel Build') {
            parallel {
                stage('Build Core') {
                    steps {
                        echo 'Building all modules (Core phase)...'
                        sh 'mvn clean install -T 2'
                    }
                }
                stage('Build API') {
                    steps {
                        echo 'Building all modules (API phase)...'
                        sh 'mvn clean install -T 2'
                    }
                }
                stage('Build Service') {
                    steps {
                        echo 'Building all modules (Service phase)...'
                        sh 'mvn clean install -T 2'
                    }
                }
                stage('Build Web') {
                    steps {
                        echo 'Building all modules (Web phase)...'
                        sh 'mvn clean install -T 2'
                    }
                }
            }
        }
    }
}
