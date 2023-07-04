pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('umerwaqasiiu-dockerhub')
    }
    stages { 

        stage('Build') {
            steps {  
                sh 'docker build -t umerwaqasiiu/docker_example .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps{
                sh 'docker push umerwaqasiiu/docker-example'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
