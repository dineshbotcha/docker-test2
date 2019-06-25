node {
    def app
    dir('docker-test') {
    deleteDir()
}

    stage('clone repo') {

        sh 'git clone https://github.com/dineshbotcha/docker-test.git'
    }


    stage('Build image') {
       
        sh 'cd docker-test'
        sh 'docker build -t dineshbotcha/docker-test .'
    }


    stage('Push image') {
        withDockerRegistry(credentialsId: 'dockerhubid', url: 'https://registry.hub.docker.com') {
           sh 'docker tag dineshbotcha/docker-test:${env.BUILD_NUMBER} docker-test:${env.BUILD_NUMBER}'
           sh 'docker tag dineshbotcha/docker-test:${env.BUILD_NUMBER} docker-test:latest'
           sh 'docker push docker-test:${env.BUILD_NUMBER}'
           sh 'docker push docker-test:latest'
            
        }
    }
   

}

