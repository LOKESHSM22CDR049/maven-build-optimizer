pipeline {
    agent any
    tools {
        maven 'Maven 3.9'  // Ensure Maven 3.9 is configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code from Git repository...'
                git credentialsId: 'github-pat', url: 'https://github.com/LOKESHSM22CDR049/maven-build-optimizer.git'
            }
        }
        stage('Parallel Build') {
            parallel {
                core {
                    steps {
                        echo 'Cleaning and building the core module...'
                        sh 'mvn -pl core clean install -am -T 2'
                    }
                }
                api {
                    steps {
                        echo 'Cleaning and building the api module...'
                        sh 'mvn -pl api clean install -am -T 2'
                    }
                }
                service {
                    steps {
                        echo 'Cleaning and building the service module...'
                        sh 'mvn -pl service clean install -am -T 2'
                    }
                }
                web {
                    steps {
                        echo 'Cleaning and building the web module...'
                        sh 'mvn -pl web clean install -am -T 2'
                    }
                }
            }
        }
        stage('Verify') {
            steps {
                echo 'Verifying the build...'
                sh 'mvn verify'
            }
        }
    }
}
