#!groovy

pipeline {
  agent none
  stages {
    
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker run hello-world'
      }
    }
  }
}
