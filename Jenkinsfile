pipeline {
    agent  { label 'linux' }
	options {
	  buildDiscarder(logRotator(numToKeepStr: '5'))}
    environment {
    DOCKERHUB_CREDENTIALS = credentials('umerwaqasiiu-dockerhub2')
    }
    stages { 

        stage('Build') {
            steps {  
                sh 'docker build -t umerwaqasiiu/dp-alpine:latest .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps{
                sh 'docker push umerwaqasiiu/dp-alpine:latest'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
