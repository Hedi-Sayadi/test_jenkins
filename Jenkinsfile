def gv
pipeline {
    agent any
    environment {
        SERVER_CREDENTIALS = credentials ('server-credentials')
    }
    stages {
        stage ("init") {
            steps {
                gv = load "script.groovy"
            }
        }
        stage("build"){
            steps {

               gv.buildApp()
                // echo 'building the app ...'
                // echo "deploying with ${SERVER_CREDENTIALS}"
            }
        }
        stage("test"){
            steps{
                echo 'testing the app ...'
            }
        }
        stage("deploy"){
            steps{
                echo 'deploying the app ...'
            }
        }
    }
}