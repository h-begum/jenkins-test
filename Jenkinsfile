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
        withCredentials([usernamePassword(credentialsId: 'deploy-anypoint-user', passwordVariable: 'ANYPOINT_CREDENTIALS_PSW', usernameVariable: 'ANYPOINT_CREDENTIALS_USR')]) {
		}
      }
      steps {
        bat 'mvn clean package deploy -DmuleDeploy -Dmule.version=4.2.1 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW}' 
      }
    }
  }
}