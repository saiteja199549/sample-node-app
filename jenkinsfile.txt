pipeline{
    agent any
    stages{
        stage('scm stage'){
           steps{
                checkout scm
            }
        }
        stage('build stage'){
            steps{
                sh "docker build -t nitinsomani/samplenodeapp ."
            }
        }
    }
}