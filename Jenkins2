pipeline {
    agent any
    environment {
        registry = "public.ecr.aws/m4s6d1u3/ecrrepo"
    }
    
    stages {
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry
        }
      }
    }
   
    stage('Pushing to ECR') {
     steps{  
         script {
                sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/m4s6d1u3'
                sh 'docker push public.ecr.aws/m4s6d1u3/ecrrepo:latest'
         }
       } 
     }      
   }
 }
      
