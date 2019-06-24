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
        app = docker.build("dineshbotcha/docker-test")
    }

    stage('Push image') {
        withDockerRegistry(credentialsId: 'dockerhubid', url: 'https://registry.hub.docker.com') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
   

}

