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
    stage("tomcat deploy"){
       steps{
         sshagent(['tomcat8']) {
    // cpoying war file to tomcat8
    sh "scp -o StrictHostKeyChecking=no target/pets-app.war ec2-user@172.31.46.97:/opt/tomcat8/webapps/"
    sh "ssh ec2-user@172.31.46.97 /opt/tomcat8/bin/shutdown.sh"
    sh "ssh ec2-user@172.31.46.97 /opt/tomcat8/bin/startup.sh"


}
       }
    }
		
	 }       
   
}


   
