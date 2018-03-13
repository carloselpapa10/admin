#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3-alpine'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    } 
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t carloselpapa10/admin:latest .'
      }
    }
  }
}
