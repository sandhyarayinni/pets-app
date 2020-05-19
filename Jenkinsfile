pipeline{
  agent any
  tools {
  maven 'maven3'
}

   stages{
     stage("mvn3"){
       steps{
        sh label: '', script: 'mvn clean package'
		}
		}
	 stage("nexus deploy"){
       steps{
       script{      
          def pomfile = readMavenPom file: 'pom.xml'
          def version = pomfile.version
          nexusrepo = version.endsWith("SNAPSHOT") ? "pets-app-snapshot" : "pets-app-release"
	        nexusArtifactUploader artifacts: [[artifactId: 'pets-app', classifier: '', file: 'target/pets-app.war', type: 'war']],
           credentialsId: 'nexus3', 
           groupId: 'in.javahome',
           nexusUrl: '18.184.92.90:8081',
           nexusVersion: 'nexus3',
           protocol: 'http',
           repository: nexusrepo, 
           version: version  
       }
	      
        
		}
		}
		
	 }       
   
}


   
