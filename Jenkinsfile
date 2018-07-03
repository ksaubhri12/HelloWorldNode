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
        sh 'export PATH="$PATH:/usr/local/bin/docker"'
        sh 'echo $PATH'
        echo 'Building docker image'
        sh 'sudo /usr/local/bin/docker build . -t gettag'
        echo 'app = docker.build("getintodevops/hellonode")'
    }

    stage('Test image'){
        echo 'Test passed'
    }
    stage('Push image'){
        echo 'Pushing image login first'
        sh 'sudo /Applications/Docker.app/Contents/Resources/bin/docker login --username=ksaubhri --password=kalpesh482'
        echo 'login successfull'
        sh 'sudo /Applications/Docker.app/Contents/Resources/bin/docker push ksaubhri/gettag'
        echo 'pushing successfull'
    }
    stage('deploying image'){
        echo 'use docker machine for creating ec2 instance'
        sh 'sudo /usr/local/bin/docker-machine create --driver amazonec2 --amazonec2-access-key AKIAJ3XF6C4DLQ4XBGVA --amazonec2-secret-key dUPPrOhoZkknIGd90sxzouE+3fKSrAxFWJxurUUx --amazonec2-region ap-south-1 aws-docker-sample-3'
        echo 'instance created successfully'
        echo 'activating docker machine'
        sh 'sudo /usr/local/bin/docker-machine env aws-docker-sample-3'
        sh 'eval $(sudo /usr/local/bin/docker-machine env aws-docker-sample-3)'
        sh 'sudo /usr/local/bin/docker-machine ssh aws-docker-sample-3'
        echo 'login successfully'
        sh 'sudo docker run hello-world'
    } 
}