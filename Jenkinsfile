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
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'cloudfoundry.org', cloudSpace: 'developer', credentialsId: 'Test@123')
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