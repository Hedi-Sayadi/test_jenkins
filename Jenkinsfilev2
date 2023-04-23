def gv
pipeline {
    agent any
    environment {
        SERVER_CREDENTIALS = credentials ('server-credentials')
    }
    stages {
        stage ("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build"){
            steps {
                script {
                    gv.buildApp()
                }

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
            input {
                message 'select the enivironment to deploy to'
                ok "Done Bro"
                parameters {
                    choice (name:'ENV',choices : ['dev','prod','staging'],description:'')
                }
            }
            steps{
                echo 'deploying the app ...'
                echo "deploying to ${ENV}"
            }
        }
    }
}