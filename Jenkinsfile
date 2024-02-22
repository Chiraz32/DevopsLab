pipeline {
  environment {
       registry = "farahsedd/DevOps-Lab"
       docker Image = ''
  }
  agent {
    dockerfile true
  }
  stages {
     stage('Pull from GitHub') {
              steps {
                  git 'https://github.com/farahsedd/DevOps-Lab.git'
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
