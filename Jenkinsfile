pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonarscanner'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonarscanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Deployment -Dsonar.ProjectName=Microservice_Deployment -Dsonar.java.binaries=.'''
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
