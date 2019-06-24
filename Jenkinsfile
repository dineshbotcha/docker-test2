pipeline {
    agent any

    stages {
        stage('Build the docker image') {
            steps{
               def  app = docker.build("dineshbotcha/docker-test")
            
        }
}
        stage('Push to docker hub'){
            steps{		
            withDockerRegistry(credentialsId: 'dockerhubid', url: 'https://registry.hub.docker.com') {
                     app.push("${env.BUILD_NUMBER}")
                     app.push("latest")      
}
        }

    }
}
}
