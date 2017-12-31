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
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'cloudfoundry.org', cloudSpace: 'developer', credentialsId: 'lakshman29')
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