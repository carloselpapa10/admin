
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
	stage('Push image') {
		/* To do that add credentials http://localhost:8080/credentials/store/system/domain/
		 * Finally, we'll push the image with two tags:
		 * First, the incremental build number from Jenkins
		 * Second, the 'latest' tag.
		 * Pushing multiple tags is cheap, as all the layers are reused. */
		docker.withRegistry('https://index.docker.io/v2/', 'docker-hub-credentials') {
		    app.push("${env.BUILD_NUMBER}")
		    app.push("latest")
		}
	}
}
