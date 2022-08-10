def imageName = 'mlabouardy/movies-loader'

/* def registry = 'https://registry.slowcoder.com' */

node('aws') {
    stage('checkout') {
        checkout scm
    }
    
    stage('unit tests') {
        def imageTest=docker.build("${imageName}-test", "-f Dockerfile.test .")
        imageTest.inside{
            sh 'python test_main.py'
        }
    }
}