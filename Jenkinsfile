// This shows a simple example of how to archive the build output artifacts.
pipeline {
        agent any
  stages{
    stage ('checkout'){
      steps{
        checkout scm
      }
    }
    stage ('Build'){
      agent {
        docker { image 'node:10' }
            }
        steps {
               echo Installing packages
               npm install
               //npm install -g @angular/cli@8
               echo Building Angular Project
               ng build
        }
    }
  }
