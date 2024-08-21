pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 echo '@@@@@@@ INSIDE BUILD @@@@@@@@ ...'
             }
             post {
                 always {
                     jiraSendBuildInfo site: 'rachellerathbone.atlassian.net'
                 }
             }
         }
     }
 }
