pipeline {
    agent {
        kubernetes {

kind: Pod
spec:
  containers:
  - name: hello-app-pod
    image: 'b6atalay/hello-app'
    imagePullPolicy: Always
    ports:
    - containerPort: 80
  restartPolicy: Always
        }
    }
}