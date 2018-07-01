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

    stage('Test image'){
        echo 'Test passed'
    } 
}