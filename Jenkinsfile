pipeline {
agent any
stages {
stage('Build1'){
    steps{
        dir('app1'){
            script{
                git 'https://github.com/cloud/simple-spring.git'
                sh 'mvn clean install'
                app = docker.build("cloud007/simple-spring")
                docker.withRegistry( "https://registry.hub.docker.com", "dockerhub" ) {
                // dockerImage.push()
                app.push("latest")
            }
        }
    }
}

}
stage('Build2'){
    steps{
        dir('app2'){
            script{
                git 'https://github.com/cloud/simple-spring-2.git'
                sh 'mvn clean install'
                app = docker.build("cloud007/simple-spring-2")
                docker.withRegistry( "https://registry.hub.docker.com", "dockerhub" ) {
                // dockerImage.push()
                app.push("latest")
            }
        }
    }
}

}
stage('Build3'){
    steps{
        dir('app3'){
            script{
                git 'https://github.com/cloud/simple-spring-3.git'
                sh 'mvn clean install'
                app = docker.build("cloud007/simple-spring-3")
                docker.withRegistry( "https://registry.hub.docker.com", "dockerhub" ) {
                // dockerImage.push()
                app.push("latest")
            }
        }
    }
}
}
stage('Orchestrate')
{
    steps{
        script{
    sh 'kubectl apply -f demo.yaml'
        }
    }
}

}
}
