pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-cred',
                        path: '',
                        url: 'http://<TOMCAT_PUBLIC_IP>:8080'
                    )
                ],
                contextPath: 'myapp',
                war: '**/*.war'
            }
        }
    }
}
