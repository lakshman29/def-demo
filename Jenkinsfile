pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
    }
    
  }
  stages {
    stage('build') {
      steps {
        bat 'mvn clean compile install'
      }
    }
  }
}