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
	     nexusArtifactUploader artifacts: [[artifactId: 'pets-app', classifier: '', file: 'target/petsapp.war', type: 'war']],
           credentialsId: 'nexus3', 
           groupId: 'in.javahome',
           nexusUrl: '35.157.129.91:8081',
           nexusVersion: 'nexus3',
           protocol: 'http',
           repository: 'pets-app-snapshot', 
           version: '1.0-SNAPSHOT'  
	      
        
		}
		}
		
	 }       
   
}


   
