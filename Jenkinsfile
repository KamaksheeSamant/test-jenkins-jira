pipeline {
	agent  any
	parameters {
	   choice choices: ['development', 'staging', 'productdion'], name: 'envs'
	}
	stages {
		stage('Build') {
		   steps {
			  echo '@@@@@@@ INSIDE BUILD @@@@@@@@ ...'
		   }
		   post {
			  always {
				 jiraSendBuildInfo site: 'kamakshee.atlassian.net'
			  }
		   }
		}
		stage("Performing deployment") {
		    steps {
			echo "@@@@@@@  Deploying to ${params.envs} environment @@@@@@@@ ..."
			jiraSendDeploymentInfo (
			    environmentId: params.envs,
			    environmentName: params.envs,
			    environmentType: params.envs,
			    serviceIds: [''],
			    site: 'kamakshee.atlassian.net',
			    state: 'successful'
			)
		     }
        	}
	}
 }
