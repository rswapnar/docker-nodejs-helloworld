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
        sh 'node server.js'
      }
    }
    stage('create image') {
      steps {
        echo 'Building..'
        
        sh 'sudo docker build -t hello-world'
        sh 'sudo docker run -p 3000:3000 -d --name server hello-world'
      }
    }
    stage('push docker image to dockerhub') {
      steps {
        echo 'pushing docker image to dockerhub..'
        sh 'sudo docker login -u "swapnar.1si15cs120@gmail.com" -p "Swapna@123"'
        sh 'sudo docker tag hello-world swapna1210/hello-world'
        sh 'sudo docker push swapna1210/hello-world'
      }
    }
  }
    
    
}
