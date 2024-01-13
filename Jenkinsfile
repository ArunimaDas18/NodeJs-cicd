pipeline {
    agent any 
    
    stages{
        stage('SCM Checkout'){
            steps {
                git url: 'xyz', branch: 'master'
            }
        }
        stage('Build '){
            steps {
                sh 'docker build . -t arunimadas18/nodejs-cicd:latest'     
            }
        }
        stage('Login and Push Image'){
            steps {
                echo 'logging in to docker hub and pushing image..'
                withCredentials([usernamePassword(credentialsId:'dockerHub',passwordVariable:'dockerHubPassword', usernameVariable:'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh "docker push arunimadas18/nodejs-cicd:latest"
                }
            }
        }
        
    }
}