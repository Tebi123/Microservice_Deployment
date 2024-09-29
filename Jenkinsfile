pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
   }

    stages {
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/adservice/') {
                        sh "docker build -t ceeepath/adservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/adservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/adservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
          stage('aws-authenticate') {
              steps {
                script {
               withAWS(credentials: 'aws_account', region: 'us-east-1') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/") {
                        sh 'aws eks --region us-east-1 update-kubeconfig --name class-eks-cluster'
                        // Replace the placeholder in the deployment.yaml file with the actual DOCKER_TAG value (edit in place)
                        sh """
                            sed -i 's|\\${DOCKER_TAG}|${DOCKER_TAG}|g' deployment.yaml
                        """
                        sh 'kubectl apply -f deployment.yaml'
                        sh 'sleep 20'
                        sh 'kubectl get pod'
                    }
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
