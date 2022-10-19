pipeline {
	agent any
  stages {
  	stage('docker Install') {
      steps {
    	sh "docker build -t welcome-app ."
	sh "docker run -it welcome-app "      	      
      }
    }
  }
}
