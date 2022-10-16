pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo 'Compiling the python code'
                sh 'docker run -it --name hello/app-in-pod b6atalay/hello-app'
            }
        }
        
    }
}