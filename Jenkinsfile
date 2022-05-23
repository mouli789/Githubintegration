pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git credentialsId: 'mouli789' , url:  'https://github.com/mouli789/Githubintegration.git'
            }
        }
        
        stage('build') {
            steps {
                sh 'docker build -t nodejsdocker . '
            }
        }

        stage('aws') {
            steps {
                sh 'docker tag nodejsdocker:latest 569381932315.dkr.ecr.ap-south-1.amazonaws.com/nodejsdocker:latest
            }
        }
        stage('aws login') {
            steps {
                sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 569381932315.dkr.ecr.ap-south-1.amazonaws.com


            }
        }

        stage('aws push') {
            steps {
                sh 'docker push 569381932315.dkr.ecr.ap-south-1.amazonaws.com/nodejsdocker:latest
            }
        }
