pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
      post {
        success {
          echo 'Now Archiving...'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
    stage('Deploy') {
      steps {
        timeout (time: 5, unit: 'DAYS') {
          input message: 'Approve StAgInG Deployment ?'
        }
        echo 'Deploying'
        build job: 'tutorial-2-to-stage' 
      }
      post {
        success {
          echo 'Code deployed to Production'
        }
        fail {
          echo 'Deploment failed.'
        }
      }
    } 
  }
}