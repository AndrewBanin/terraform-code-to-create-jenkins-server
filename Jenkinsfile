pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID_&_AWS_SECRET_ACCESS_KEY = credentials('awsaccess&secretkeys')
        // AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_DEFAULT_REGION = "us-east-1"
    }
}
    stages {
        stage("Create an EKS Cluster using eksctl") {
            steps {
                script {
                    dir('eksctl') {
                        sh "eksctl create cluster --name banina --region us-east-1 --with-oidc --nodegroup-name banina-workers --version 1.24 --nodes 4 --nodes-min 2 --nodes-max 4 --instance-types=t2.medium --managed"
                        sh "aws eks update-kubeconfig --region us-east-1 --name banina"
                    }
                }
            }
        }
    }
//         stage("Deploy to EKS") {
//             steps {
//                 script {
//                     dir('kubernetes') {
//                         sh "aws eks update-kubeconfig --name myapp-eks-cluster"
//                         sh "kubectl apply -f nginx-deployment.yaml"
//                         sh "kubectl apply -f nginx-service.yaml"
//                     }
//                 }
//             }
//         }
//     }
// }