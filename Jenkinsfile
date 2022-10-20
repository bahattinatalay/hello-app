pipeline {
	agent any
  stages {
        stage('docker Build') {
            steps {
                sh "docker build -t b6atalay/welcome-app3 ."
            }
      }
  
        stage('Docker Push') {
        steps {
                sh "docker login -u ${env.Username} -p ${env.Password}"
            sh 'docker push b6atalay/welcome-app3'
        }

        agent any

        tools {
            dockerTool 'docker-jenkins'
        }
        }


        stage('Deploy on Kubernetes') {
        steps {
            sh 'kubectl apply -f .'
        }

        options {
            withKubeConfig(caCertificate: '', clusterName: 'kubernetes', contextName: 'kubernetes-admin@kubernetes', credentialsId: 'jenkins-k8s', namespace: 'kube-system', serverUrl: 'https://172.31.8.195:6443')
        }
        }
 }
}