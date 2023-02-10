pipeline {

    
        stages {
         stage('Build') {
             steps {
                 echo 'Building...'
             }
             post {
                 always {
                     jiraSendBuildInfo site: 'https://firstjirasite.atlassian.net' , branch: 'FIR-4'
                 }
             }
         }

        

    }   
}

