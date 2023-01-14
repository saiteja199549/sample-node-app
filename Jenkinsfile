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
		    sh 'docker build -t saiteja199549/samplenodeapp:${BUILD_NUMBER} .'
            }
        }
        stage('push stage'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push saiteja199549/samplenodeapp:${BUILD_NUMBER}'
            }
        }
        stage('deploy stage'){
            steps{
                sh 'docker container run -itd -p 3000:3000 saiteja199549/samplenodeapp:${BUILD_NUMBER}'
            }
        }
    }
    post{
        always{
            sh 'docker logout'
        }
    }
}
