pipeline {
  agent any
  stages{
    stage ('checkout') {
      steps{
        checkout scm
      }
    }
    stage ('Build') {
      agent {
        docker { image 'node:10'}
      }
      steps {
        sh 'echo installing packages'
        sh 'npm install'
        sh 'npm install -g @angular/cli@8'
        sh 'echo Building Angular Project'
        sh 'ng build'

      }
    }
    stage ('push') {
      steps{
   withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'angular', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        sh 'aws s3 ls'
        sh 'aws s3 sync . s3://sample-angular-demo/ --region us-east-2'
        }
        sh 'echo pushing success'
      }
    }

  }
}
