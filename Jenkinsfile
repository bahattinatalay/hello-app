pipeline {
agent any

  stages{
    stage ('Build') {
      steps {
        kubernetes {
          label 'hello-app'
          defaultContainer 'hello-app-pod'          
          yaml ''' 
apiVersion: apps/v1 
kind: Deployment 
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
}
}
}