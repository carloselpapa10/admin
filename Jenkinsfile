
node {
	def app

        stage('Clone repository') {
        	/* Let's make sure we have the repository cloned to our workspace */
		checkout scm
        }
        stage('Build'){
		/* add a tool in the Jenkins "Global Tool Configuration" and refer the name */
		def mvnHome = tool 'maven-3'
		sh "${mvnHome}/bin/mvn clean install -DskipTests"
		stash 'working-copy'
	}
        stage('Build image') {
        	/* This builds the actual image; synonymous to
                * docker build on the command line */
		app = docker.build("carloselpapa10/admin")
        }
}
