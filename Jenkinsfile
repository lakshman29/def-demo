pipeline {
  agent any
  stages {
    stage('') {
      steps {
        bat 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }
  }
  environment {
    maven = 'mvn '
    jdk = 'java'
  }
}