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

		stage ('Deploy to production'){
			steps{
				timeout (time: 5, unit: 'Days'){
					input message: 'Approve PRODUCTION deployment?'

				}
				build job : 'deploy-prod-pipeline'
			}
			post {
				success {
					echo 'PRODUCTION deployment successful'
				}
				failure {
					echo 'PRODUCTION deployment failed'
				}	
			}

		}
		
	}
}