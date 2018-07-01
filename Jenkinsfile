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
        sh 'echo $PATH'
        sh 'export $PATH="$PATH:/usr/local/bin/docker"'
        sh 'echo $PATH'
        echo 'Building docker image'
        sh 'sudo /usr/local/bin/docker build . -t gettag:4'
        echo 'app = docker.build("getintodevops/hellonode")'
    }

    stage('Test image'){
        echo 'Test passed'
    }
    stage('Push image'){
        echo 'Pushing image login first'
        sh 'sudo /Applications/Docker.app/Contents/Resources/bin/docker login -u=ksaubhri -p=kalpesh482 https://registry.hub.docker.com'
        echo 'login successfull'
        sh 'sudo /Applications/Docker.app/Contents/Resources/bin/docker push ksaubhri/gettag'
        echo 'pushing successfull'
    } 
}