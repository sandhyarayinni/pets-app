pipeline{
  agent any

   stages{
     stage("git checkout"){
     steps{
        git credentialsId: 'github', url: 'https://github.com/sandhyarayinni/pets-app'
   }
   }
   stage("mvn3"){
     steps{
        sh label: '', script: 'mvn clean package'
   }
   }
   }
}
   
