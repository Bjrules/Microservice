pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'babade-cluster', contextName: '', credentialsId: 'K8s', namespace: 'webapps', serverUrl: 'https://AA65A6705A374B8491271FACD9F9AF4E.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 30
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'babade-cluster', contextName: '', credentialsId: 'K8s', namespace: 'webapps', serverUrl: 'https://AA65A6705A374B8491271FACD9F9AF4E.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
