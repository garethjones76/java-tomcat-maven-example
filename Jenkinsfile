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
		stage ('Deploy Build to staging area') {
			steps {
				build job :  'servlet_deploy_staging_pipe'
			}
		}
		
	}
}