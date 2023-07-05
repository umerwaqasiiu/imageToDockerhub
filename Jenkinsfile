pipeline {
    agent any 
    options {
	buildDiscarder(logRotator(numToKeepStr: '5'))
            }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('umerwaqasiiu-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t umerwaqasiiu/dp-alpine:latest .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
            sh 'docker push umerwaqasiiu/dp-alpine:latest'
            }
        }

	      stage('logout') {
            steps{
                sh 'docker logout'
            }
        }
}

}
