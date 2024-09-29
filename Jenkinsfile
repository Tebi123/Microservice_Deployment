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
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/microservice/src/adservice/') {
                        sh "docker build -t ceeepath/adservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/adservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/adservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
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
