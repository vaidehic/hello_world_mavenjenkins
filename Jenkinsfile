pipeline {

    agent any
        stages {
         stage('Build') {
             steps {
                 echo 'Building...'
             }
             post {
                 always {
                    
                     jiraSendBuildInfo branch: 'FIR-4', site: 'firstjirasite.atlassian.net'
                 }
             }
         

        }

    }   
}

