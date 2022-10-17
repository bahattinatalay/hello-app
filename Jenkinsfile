pipeline {
  agent {
    kubernetes {
      yaml '''

apiVersion: v1 
kind: Pod
metadata:
  name: hello-app-deploy
spec:
  replicas: 1 
  selector:  
    matchLabels:
      app: hello
  minReadySeconds: 10 
  strategy:
    type: RollingUpdate 
    rollingUpdate:
      maxUnavailable: 1 
      maxSurge: 1 
  template: 
    metadata:
      labels:
        app: hello    
    spec:
      containers:
      - name: hello-app-pod
        image: b6atalay/hello-app
        ports:
        - containerPort: 80
        command: ['python','welcome.py']
'''

      }
    }
    
    stages {
        stage('Build ') {
            steps {
                checkout scm {
                        sh "kubectl apply -f . "
                    }
                }
            }
        }
    }