#!groovy
properties ([disableConcurrentBuilds()])

pipeline {
    agent any
    triggers {pollSCM("* * * * *")}
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr:'10'))
        timestamps()
    }
    stages {
        stage('docker login') {
            steps {
                echo "=========================docker login =================="
                withCredentials([usernamePassword(credentialsId:'dockerhub_kav0484', usernameVariable: 'USERNAME',passwordVariable: 'PASSWORD')])
                sh 'docker login -u $USERNAME -p $PASSWORD' 
            }
        }
        stage("create docker image") {
            steps {
                echo "================start build image============"
                dir ('docker/toolbox') {
                    sh 'docker build -t kav0484/toolbox:latest .'
                }
            }
        }
        stage('docker push') {
            steps {
                echo "=====================start pushing image===================="
                sh 'docker push kav0484/toolbox:latest' 
            }
        }
    }
}