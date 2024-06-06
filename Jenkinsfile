pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://19DCC08B4BE5813CD0E41AC47AE13D84.sk1.ap-south-1.eks.amazonaws.com']) {
                        sh "kubectl apply -f deployment-service.yml"
                        sleep 60
                    }
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://19DCC08B4BE5813CD0E41AC47AE13D84.sk1.ap-south-1.eks.amazonaws.com']) {
                        sh "kubectl get all -n webapps"
                    }
                }
            }
        }
    }
}
