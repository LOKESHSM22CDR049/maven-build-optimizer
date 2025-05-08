pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8' // Ensure this Maven version is installed in Jenkins
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
                        echo 'Cleaning and building the core module...'
                        sh 'mvn -pl core clean install -am -T 2'
                    }
                }
                stage('Build API') {
                    steps {
                        echo 'Cleaning and building the api module...'
                        sh 'mvn -pl api clean install -am -T 2'
                    }
                }
                stage('Build Service') {
                    steps {
                        echo 'Cleaning and building the service module...'
                        sh 'mvn -pl service clean install -am -T 2'
                    }
                }
                stage('Build Web') {
                    steps {
                        echo 'Cleaning and building the web module...'
                        sh 'mvn -pl web clean install -am -T 2'
                    }
                }
            }
        }
    }
}
