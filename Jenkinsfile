#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Clean Package') {
      agent {
        docker {
          image 'maven:3-alpine'
        }
      }
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    } 
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t carloselpapa10/admin:latest .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'Hardtech-c01', usernameVariable: 'carloselpapa10')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push carloselpapa10/admin:latest'
        }
      }
    }
  }
}
