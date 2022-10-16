pipeline {
agent any

  stages{
    stage ('Build') {
      steps {
        kubernetes {
          label 'hello-app'
          defaultContainer 'hello-app-pod'          
          yaml ''' 
apiVersion: v1           
kind: Pod
spec:
  containers:
  - name: "hello-app-pod"
    image: 'b6atalay/hello-app'
    imagePullPolicy: Always
    ports:
    - containerPort: 80
  restartPolicy: Always
'''
        }
    }
}
}
}