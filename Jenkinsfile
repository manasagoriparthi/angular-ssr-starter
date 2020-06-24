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

      }
    }

  }
}
