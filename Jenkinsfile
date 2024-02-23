pipeline {
  environment {
       registry = "Chiraz32/DevopsLab"
       DOCKER_CREDENTIALS = credentials('dockerhub-credentials')
  }
 agent any
  stages {
     stage('Pull from GitHub') {
              steps {
                  git 'https://github.com/Chiraz32/DevopsLab.git'
              }
     }
       stage('Build Docker image') {
                 steps {
                     script {
                         docker.build("${registry}:1.3")
                     }
                 }
             }


      stage('Login to Docker Hub') {
                   steps{
                             withCredentials([string(credentialsId: 'dockerHubPassword', variable: 'dockerHubPassword')]) {
                     	    sh 'docker login -u chirazdoss -p ${dockerHubPassword}'
                             echo 'Login Completed'
                          }
                         }
                     }

       stage('Push to DockerHub') {
                 steps {
                     sh 'docker push ${registry}:1.3'
                     echo 'Push Image Completed'
                 }
             }

  }

}
