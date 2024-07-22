pipeline {
    agent any

    stages {
        stage('Depoy to k8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6BE5882FD0774211E36FDF62DD51C468.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
               }
            }
        }    
        
    stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6BE5882FD0774211E36FDF62DD51C468.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl get all -n webapps"
                  
               }
            }        
        
        }
        
    }
    
}

