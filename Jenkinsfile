pipeline {
    agent any
    stages {
        stage('clean workspace'){

         steps {
                cleanWs()
            }
        }
        stage('clone repo'){
          steps{
               
             sh 'git clone https://github.com/dineshbotcha/docker-test.git'

}
}
        stage('Build image') {
            steps {
                echo 'Starting to build docker image'
                sh '''
                    cd docker-test
                    export PATH=/usr/local/bin:$PATH
                    docker version
                    echo $PATH'''
                script {

                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                    
                }
            }
        }
    }
}
