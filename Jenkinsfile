pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'gke-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '34.93.114.85']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'gke-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '34.93.114.85']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
