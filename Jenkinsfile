pipeline {
	agent any
  stages {
    stage('docker Build and Install') {
       steps {
    	sh "docker build -t welcome-app2 ."
	sh "docker run --name hello-task -d -p 80:80 welcome-app2 "
	
      }
    }
       stage('Docker Push') {
    	agent any
         steps {
      	withCredentials([usernamePassword(credentialsId: 'docker-login', passwordVariable: 'Password', usernameVariable: 'Username')]) {
        	sh "docker login -u ${env.Username} -p ${env.Password}"
                sh 'docker push b6atalay/welcome-app2:latest'
 	 }
       }
     }
   }
}
