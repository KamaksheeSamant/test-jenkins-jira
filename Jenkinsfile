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
		stage('deploy to DEV') {
            		when { expression { "$params.envs" == "development" } } 
            		steps {                
				echo "@@@@@@@  Deploying to ${params.envs} environment @@@@@@@@ ..."               
            		}
            		post { 
                		always { 
                    			// TODO this does NOT work - the JtoJ plygin does not parse out the Jira key correctly
                    			jiraSendDeploymentInfo environmentId: params.envs, environmentName: params.envs, environmentType: params.envs, site: 'kamakshee.atlassian.net'
                		}	 
            		}	             
        	}
	}
 }
