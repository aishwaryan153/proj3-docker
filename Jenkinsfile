pipeline {
    agent any 

    stages {
        stage ('Checkout') {
           steps {
               git branch: 'main',
                  url: 'https://github.com/aishwaryan153/proj3-docker.git'
                 }
           }

        stage ('Build Docker Image') {
            steps {
               sh 'docker build -t project3:latest .'
             }
          }

        stage ('Tag docker image') {
            steps {
                sh 'docker tag project3:latest aishwaryalaxmi0599/project3:latest'
            }
        }

       stage ('Login to docker hub'){
           steps {
               withCredentials([
                   usernamePassword(
                       credentialsId: 'dockerhub-credentials'
                       usernameVariable: 'DOCKER_USERNAME'
                       passwordVariable: 'DOCKER_PASSWORD'
                     )
                 ]){
                      sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin
               }
             }
           }

        stage ('Push Docker Image') {
            steps {
                sh 'docker push aishwaryalaxmi0599/project3:latest'
            }
        }
     }     
}
}
