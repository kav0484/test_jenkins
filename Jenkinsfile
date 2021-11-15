pipeline {
    agent any
    stages{
        stage('build'){
            steps{
                sh 'mvn clean install'
            }
        }
    }
    post {
        always {
            mail to: "[kav0484@mail.ru]",
                subject: "Build finished: ${currentBuild.fullDisplayName}",
                body: "Check out status at ${env.BUILD_URL}"
        }
    }
}