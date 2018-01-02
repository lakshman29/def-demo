pipeline {
  agent any
  stages {
     stage('clean') {
      steps {
        bat 'mvn clean'
      }
      
    }
    stage('build') {
      steps {
        bat 'mvn -Dmaven.test.skip=true install'
      }
      
    }
    stage('Test') {
      steps{
            bat 'mvn test'
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
