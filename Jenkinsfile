pipeline{
    agent any
    tools{
        maven "Maven 3.6.3"
        jdk "JDK-11"
    }       
    stages {

        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }

        stage('Compile'){
            steps{
                echo "COMPILE"
             bat 'mvn clean install'
            }
        }
        stage('Sonar Analysis') {
            steps {
                // use the SonarQube Scanner to analyze the project
                withSonarQubeEnv('SonarQubeServer') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
        
        stage('Upload Artifact') {
              steps {
                  script{
                      def server = Artifactory.server 'JfrogServer'
                      def uploadSpec = """{ 
                          "files":[
                              {
                                  "pattern":"target./*.jar",
                                  "target": "Simple_java_project_Repo/"
                              }
                              }
                              }"""
                              server.upload(uploadSpec)
                              }
                              }
                              }
                          
        }
    
}

