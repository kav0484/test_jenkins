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
        stage("create docker image") {
            steps {
                echo "================start build image============"
                dir ('docker/toolbox') {
                    sh 'docker build -t toolbox:latest .'
                }
            }
        }
    }
}