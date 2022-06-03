#! /usr/bin/env groovy

pipeline {

  agent {
    label 'nodejs'
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        
        sh 'npm install'
        //sh 'node server.js'
      }
    }
    stage('create image') {
      agent any
      steps {
        echo 'Building..'
        
        sh 'docker build -t hello-world .'
        sh 'docker run -p 3000:3000 -d --name server hello-world'
      }
    }
    stage('push docker image to dockerhub') {
     /* steps {
        
        echo 'pushing docker image to dockerhub..'
        sh 'docker login -u "swapnar.1si15cs120@gmail.com" -p "Swapna@123"'
        sh 'docker tag hello-world swapna1210/hello-world'
        sh 'docker push swapna1210/hello-world'
      }*/
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'Swapna@123', usernameVariable: 'swapnar.1si15cs120@gmail.com')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push swapna1210/hello-world'
        }
    }
  }
    
  }  
}
