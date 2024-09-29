pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Deployment -Dsonar.ProjectName=Microservice_Deployment -Dsonar.java.binaries=.'''
                }
            }
        }
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
            stage('cartservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/cartservice/src/") {
                        sh "docker build -t ceeepath/cartservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/cartservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/cartservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
       }
            stage('checkoutservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/checkoutservice/") {
                        sh "docker build -t ceeepath/checkoutservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/checkoutservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/checkoutservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('currencyservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/currencyservice/") {
                        sh "docker build -t ceeepath/currencyservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/currencyservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/currencyservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }

            }
            stage('emailservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/emailservice/") {
                        sh "docker build -t ceeepath/emailservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/emailservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/emailservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('frontend') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/frontend/") {
                        sh "docker build -t ceeepath/frontend:${DOCKER_TAG} ."
                        sh "docker push ceeepath/frontend:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/frontend:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('loadgenerator') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/loadgenerator/") {
                        sh "docker build -t ceeepath/loadgenerator:${DOCKER_TAG} ."
                        sh "docker push ceeepath/loadgenerator:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/loadgenerator:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
             stage('paymentservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/paymentservice/") {
                        sh "docker build -t ceeepath/paymentservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/paymentservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/paymentservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('productcatalogservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/productcatalogservice/") {
                        sh "docker build -t ceeepath/productcatalogservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/productcatalogservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/productcatalogservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('recommendationservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/recommendationservice/") {
                        sh "docker build -t ceeepath/recommendationservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/recommendationservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/recommendationservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('shippingservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/shippingservice/") {
                        sh "docker build -t ceeepath/shippingservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/shippingservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/shippingservice:${DOCKER_TAG}"
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
