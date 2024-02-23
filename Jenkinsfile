pipeline {
  environment {
       registry = "Chiraz32/DevopsLab"
       registryCredential = 'docker'
      
  }
  agent any
  stages {
     stage('Build') {
       steps {
        script {docker Image =docker.build registry + ":$BUILD_NUMBER"}
       }
  }
  stage('Push') {
     steps {
        script {
            docker.withRegistry( '', registryCredential ) {
                  dockerImage.push()
            }

        }
     }
  }

   stage('Run') {
     steps {
       script {  dockerImage.run("-p 80:4200 ")
       }
     }
   }
 }

}
