pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('Dockerhub credentials')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh ' docker build -t tomcat:works .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push tomcat:works'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
