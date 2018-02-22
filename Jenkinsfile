pipeline {
  agent any

  tools {
    maven: maven
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
        echo 'Deploying'
      }
    } 
  }
}