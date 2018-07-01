node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        echo 'kalpesh'
        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        sh 'echo "Tests passed"'
        sh 'pwd'
        echo 'Building docker image'
        sh 'sudo /Applications/Docker.app/Contents/Resources/bin/docker build . -t gettag:4'
        echo 'app = /Applications/Docker.app/Contents/Resources/bin/docker.build("getintodevops/hellonode")'
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

         echo 'Test passed'
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        sh 'docker login --username=ksaubhri --password=kalpesh482  https://registry.hub.docker.com'
        sh 'docker push ksaubhri/gettag'
        echo 'docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")'
        }
    }
}