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
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'docker-hub-pass', usernameVariable: 'docker-hub-usr')]) {
          sh "docker login -u docker-hub-usr -p docker-hub-pass"
          sh 'docker push carloselpapa10/admin:latest'
        }
      }
    }
  }
}
