pipeline {
  agent any
  stages{
    stage ('checkout') {
      steps{
        checkout scm
        sh 'apt-get update && apt-get install -y docker.io '
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
