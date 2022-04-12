pipeline {
  // agent { label 'linux'}
  agent any
  options {
    skipDefaultCheckout(true)
  }
  tools {
        terraform 'terraform'
    }
  stages{
    stage('clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('terraform') {
      steps {
        bat './terraform apply -auto-approve -no-color'
        //sh './terraformw apply -auto-approve -no-color'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
