pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
   }

    stages {
      stage('aws-authenticate') {
              steps {
                script {
               withAWS(credentials: 'aws_account', region: 'us-east-1') {
                    sh 'aws eks --region us-east-1 update-kubeconfig --name class-eks-cluster'
                    sh 'kubectl run nginx --image=nginx'
                    sh 'sleep 10'
                    sh 'kubectl get pod'
                }
            }
        }
      }
    }
    post {
        always {
            echo "Pipeline completed!"
    }
  }
}
