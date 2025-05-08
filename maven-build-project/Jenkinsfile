pipeline {
    agent any
    tools {
        maven 'Maven 3.9'  // Make sure Maven 3.9 is installed in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', url: 'https://github.com/LOKESHSM22CDR049/maven-build-optimizer.git'
            }
        }
        stage('Parallel Build') {
            parallel {
                core {
                    steps {
                        sh 'mvn -pl core clean install -am -T 2'  // Run build for the core module in parallel
                    }
                }
                api {
                    steps {
                        sh 'mvn -pl api clean install -am -T 2'  // Run build for the api module in parallel
                    }
                }
                service {
                    steps {
                        sh 'mvn -pl service clean install -am -T 2'  // Run build for the service module in parallel
                    }
                }
                web {
                    steps {
                        sh 'mvn -pl web clean install -am -T 2'  // Run build for the web module in parallel
                    }
                }
            }
        }
        stage('Verify') {
            steps {
                sh 'mvn verify'  // Verify the build after all parallel tasks
            }
        }
    }
}
