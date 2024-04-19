pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/venugopalsgnew/kubernetes-training.git'
            }
        }

        stage('Deploy nginx on to k8 Cluster') {
            steps {
                script {
                  kubeconfig(credentialsId: 'KUBE_CONFIG', serverUrl: 'https://172.31.33.136:6443') {
                    sh 'kubectl apply -f deployment.yaml'
                }

                }

            }
        }
    }
}
