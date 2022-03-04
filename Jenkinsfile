pipeline{
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-credentials')
	}
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
        stage('push stage'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh "docker push nitinsomani/samplenodeapp:latest"
            }
        }
    }
    post{
        always{
            sh 'docker logout'
        }
    }
}