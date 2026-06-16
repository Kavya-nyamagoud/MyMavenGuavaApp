pipeline {
    agent any  

    tools {
        maven 'Maven'
    }

    

    stages {

        stage('Checkout') {
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

       

        stage('Run Application') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass="com.example"'
                
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
