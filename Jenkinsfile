pipeline {
	agent any
	stages {
		
		stage ('Build') {
			def mvn_version = 'M2'
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