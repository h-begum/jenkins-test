pipeline {
  agent any
  stages {
    stage('Unit Test') { 
      steps {
        bat 'mvn clean test'
      }
      }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('deploy-anypoint-user')
      }
      steps {
        bat "mvn clean package deploy -DmuleDeploy -Dmule.version=4.3.0 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}"
      }
    }
  }
}
