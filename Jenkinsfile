pipeline {
    agent any
    tools {
        maven 'maven-3.8.6' 
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-credentials')
    } 
    stages {
        stage ("build jar") {
            steps {
                script {
                    echo 'building the application'
                    sh 'mvn package'
                }
            }
        }
        stage("build docker image"){
            steps {
               script {
                    echo 'building the docker image'
                    // withCredentials([useramePassword(credentialsId:'docker-hub-credentials',passwordVariable:'PASS',usenameVariable:'USER')]){
                        sh 'docker build -t hedisayadi/test_CICD:1.0 .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        // sh "echo $PASS | docker login -u $USER --password -stdin"
                        sh 'docker push hedisayadi/test_CICD:1.0'
                    // }
                }
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
                // echo "deploying to ${ENV}"
            }
        }
    }
}