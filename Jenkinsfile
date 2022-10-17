pipeline {
	agent any
  stages {
  	stage('docker Install') {
      steps {
    	sh "docker build -t welcome-app ."
      }
    }
  }
}