pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://66296434A9949C56570A984A158E2421.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://66296434A9949C56570A984A158E2421.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
