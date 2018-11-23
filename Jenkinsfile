pipeline {
	agent any
	stages {
		def mvn_version = 'M2'
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