node {
    def app
    stage('clone repo') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        sh 'git clone https://github.com/dineshbotcha/docker-test.git'
    }


    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("dineshbotcha/docker-test")
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        withDockerRegistry(credentialsId: 'dockerhubid', url: 'https://registry.hub.docker.com') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
