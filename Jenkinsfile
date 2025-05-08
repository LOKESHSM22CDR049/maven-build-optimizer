pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6' // or whatever you named it in Jenkins -> Global Tool Config
        jdk 'Java 17'       // your configured JDK
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/maven-build-optimizer.git'
            }
        }

        stage('Build with Parallel Execution') {
            steps {
                sh 'mvn -T 1C clean install'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully with parallel execution!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
