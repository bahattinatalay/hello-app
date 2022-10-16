pipeline {
    agent none
  stages {
    stage('docker run') {
        agent {
        docker {
            image 'b6atalay/hello-app'
        }
      }
      steps {
        echo 'Pulling the welcome image'
      }
    }
    stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker run -it --name hello/app-in-pod -p b6atalay/hello-app'
      }
    }
  }
}