pipeline {
    agent { 
	docker {
            image 'maven:3-alpine'
        }
    }
    stages {
	
	    stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('other') { 
            node {
                def app

                stage('Clone repository') {
                    /* Let's make sure we have the repository cloned to our workspace */

                    checkout scm
                }
                stage('clean install'){
                      sh 'mvn --version'

                }
                stage('Build image') {
                    /* This builds the actual image; synonymous to
                     * docker build on the command line */

                    //app = docker.build("carloselpapa10/admin")
                }
            }
        }
    
	
    }
}
