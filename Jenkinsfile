pipeline {

  agent any
  environment {
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.3.0'
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            sh 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Deploy Sandbox') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'timezone-api-cicdpipeline'
      }
      steps {
            sh 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy'
      }
    }
  }

  tools {
    maven 'M3'
  }
}
