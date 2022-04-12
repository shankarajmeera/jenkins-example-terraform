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
    stage("terraform init"){
            steps{
               bat 'terraform init'
            }
        }
    stage('terraform apply') {
      steps {
         bat 'terraform apply -auto-approve'
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
