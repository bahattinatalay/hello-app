pipeline {
	agent any
  stages {
   stage('docker Build') {
       steps {
    	sh "docker build -t b6atalay/welcome-app3 ."
//	   sh "docker run --name hello-task -d -p 80:80 b6atalay/welcome-app3 "
	
      }
    }
   stage('Docker Push') {
    	agent any
         steps {
      	withCredentials([usernamePassword(credentialsId: 'docker-login', passwordVariable: 'Password', usernameVariable: 'Username')]) {
      sh "docker login -u ${env.Username} -p ${env.Password}"
      sh 'docker push b6atalay/welcome-app3'
 	 }
       }
     }
   stage('Deploy on Kubernetes') {
       steps {
    	sh "kubectl apply -f ."
      }
    }
   }
}
