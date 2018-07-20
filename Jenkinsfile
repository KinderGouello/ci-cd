pipeline {
  agent {
    docker { image 'node:8-alpine' }
  }
  stages {
    stage('build') {
      steps {
        checkout scm
        sh 'npm install'
      }
    }
    stage('test') {
      steps {
        sh 'npm run lint'
        sh 'npm run test:unit'
      }
    }
    stage('teste2e') {
      agent {
        docker { image 'cypress/base:8' }
      }
      steps {
        sh 'npm run test:e2e:headless'
      }
    }
  }
}
