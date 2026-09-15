pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'e-commerece', contextName: '', credentialsId: 'k8s-cred', namespace: 'ecom', serverUrl: 'https://1C08C7283016D6D2F96728ED67155534.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'e-commerece', contextName: '', credentialsId: 'k8s-cred', namespace: 'ecom', serverUrl: 'https://1C08C7283016D6D2F96728ED67155534.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n ecom"
                }
            }
        }
    }
}
