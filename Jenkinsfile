pipeline {
  agent any
  tools {
        maven 'mvn'
        jdk 'jdk8'
    }
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
