pipeline {
    agent any

    tools {
        maven 'Maven'   // Make sure Maven is configured in Jenkins
        jdk 'JDK'      // Change based on your setup
    }

    environment {
        APP_NAME = "MyGuavaApp"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/Kavya-nyamagoud/MyMavenGuavaApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${APP_NAME}..."
                // Example deployment (customize this)
                sh 'cp target/*.jar /opt/myguava-app/'
            }
        }
    }

    post {
        success {
            echo 'Build Successful '
        }
        failure {
            echo 'Build Failed '
        }
    }
}
