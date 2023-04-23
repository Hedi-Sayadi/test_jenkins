pipeline {
    agent any
    tools {
        maven 'maven-3.8.6'
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
                    sh 'mvn package'
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
                echo "deploying to ${ENV}"
            }
        }
    }
}