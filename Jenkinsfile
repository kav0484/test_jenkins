#!groovy
properties ([disableConcurrentBuilds()])

pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr:'10'))
        timestamps()
    }
    stages {
        stage("Preparations") {
            steps {
                sh 'ssh d11test \'hostname\''
            }
        }
    }
}