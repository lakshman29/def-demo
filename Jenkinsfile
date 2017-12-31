pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
    }
    
  }
  stages {
    stage('build') {
      steps {
        bat 'clean compile install'
      }
    }
  }
}