def imageName = 'mlabouardy/movies-loader'

/* def registry = 'https://registry.slowcoder.com' */

node('aws') {
    stage('checkout') {
        checkout scm
    }
    
    stage('Unit test'){
        def imageTest= docker.build("${imageName}-test", "-f Dockerfile.test .")
        sh "docker run --rm -v $PWD/reports:/app/reports ${imageName}-test"
        sh "junit /var/lib/jenkins/reports/*.xml"
    }
}