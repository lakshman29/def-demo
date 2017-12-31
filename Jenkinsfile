pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }
    stage('push') {
      steps {
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'cloudfoundry.org', cloudSpace: 'development', credentialsId: 'public-cloud')
      }
    }
    stage('userinput') {
      steps {
        input(message: 'shall we deploy to cloud foundry', id: 'yes', ok: 'no')
      }
    }
  }
  tools {
    maven 'mvn'
    jdk 'jdk8'
  }
  environment {
    maven = 'mvn '
    jdk = 'java'
  }
}