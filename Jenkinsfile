pipeline {
    agent any
    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker build -t bjrules/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image to hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker push bjrules/adservice:latest "
                    }
                }
            }
        }
    }
}
