pipeline {
	agent any
  stages {
  	stage('docker Install') {
      steps {
    	sh "docker build -t welcome-app ."
	sh "docker run --name hello-task -d -p 80:80 welcome-app "      	      
      }
    }
  }
}
