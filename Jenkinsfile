pipeline {
	agent any
  stages {
   stage('docker Build') {
       steps {
    	 sh "docker build -t b6atalay/welcome-app3 ."
       }
      }
    
   stage('Docker Push') {
    	agent any
         steps {
      	withCredentials([usernamePassword(credentialsId: 'docker-login', passwordVariable: 'Password'), usernameVariable: 'Username']) 
      sh "docker login -u ${env.Username} -p ${env.Password}"
      sh 'docker push b6atalay/welcome-app3'
 	 }
       }
     
   stage('Deploy on Kubernetes') {
    	agent any
       steps  {
        withKubeConfig(caCertificate: '', clusterName: 'kubernetes', contextName: 'kubernetes-admin@kubernetes', credentialsId: 'jenkins-k8s', namespace: 'kube-system', serverUrl: 'https://172.31.8.195:6443') {
    	
        sh 'kubectl apply -f .'       }
       }    
   }
  
}
}