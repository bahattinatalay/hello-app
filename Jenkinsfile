pipeline {
	agent none
  stages {
  	stage('docker Install') {
      steps {
    	sh "docker build -t welcome-app ."
      }
    }
  }
}