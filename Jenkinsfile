pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'mvn -Dmaven.test.failure.ignore=true install'
      }
      post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
    }
    
    stage('Approve') {
      steps {
        input(message: 'shall we deploy to cloud foundry', id: 'userinput', ok: 'YES')
      }
    }
    stage('push') {
      steps {
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'cloudfoundry.org', cloudSpace: 'development', credentialsId: 'public-cloud')
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
