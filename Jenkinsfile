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
                    sh 'aws iam get-user'
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
