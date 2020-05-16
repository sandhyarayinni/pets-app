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
   }
}
   
