pipeline {
	agent any
	tools {
    	maven 'LocalMaven'
  	}
	stages {
		
		stage ('Build') {
			steps {
				sh 'mvn clean package'
			}
			post {
				success {
					echo 'now archiving'
					archiveArtifacts artifacts : '**/*.war'
				}
			}
		}

		
	}
}