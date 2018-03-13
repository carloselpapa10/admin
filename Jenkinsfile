node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    stage('clean install'){
        //agent { docker 'maven:3-alpine' } 
        steps {
            echo 'Hello, Maven'
            //sh 'mvn --version'
        }
    }
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        //app = docker.build("carloselpapa10/admin")
    }
}
