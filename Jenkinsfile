def imageName = 'mlabouardy/movies-loader'

/* def registry = 'https://registry.slowcoder.com' */

node('aws') {
    stage('checkout') {
        checkout scm
    }
    
    stage('unit tests') {
        sh "docker build -t ${imageName}-test -f Dockerfile.test ."
        sh "docker run --rm -v $PWD/reports:/app/reports ${imageName}-test"
        sh "junit $PWD/reports/*.xml"
    }
}