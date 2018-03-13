
node {
	def app

        stage('Clone repository') {
        	/* Let's make sure we have the repository cloned to our workspace */
		checkout scm
		
		def mvnHome = tool 'maven-3'
		sh "${mvnHome}/bin/mvn clean install -DskipTests"
		stash 'working-copy'
        }
        stage('clean install'){
		withMaven(
			// Maven installation declared in the Jenkins "Global Tool Configuration"
			maven: 'M3',
			// Maven settings.xml file defined with the Jenkins Config File Provider Plugin
			// Maven settings and global settings can also be defined in Jenkins Global Tools Configuration
			mavenSettingsConfig: 'my-maven-settings',
			mavenLocalRepo: '.repository') {

		      // Run the maven build
		      sh "mvn clean install"

		    }
	}
        stage('Build image') {
        	/* This builds the actual image; synonymous to
                * docker build on the command line */

                //app = docker.build("carloselpapa10/admin")
        }
}
