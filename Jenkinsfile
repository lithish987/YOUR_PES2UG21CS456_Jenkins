pipeline {
  agent any 
  stages {
          stage('Clone repository') {
              steps {
                  checkout([$class: 'GitSCM',
                  branches: [[name:'*/main']],
                  userRemoteConfigs: [[url: 'https://github.com/lithish987/YOUR_PES2UG21CS456_Jenkins.git']]])
                  }  
              }
  stage('Build') {
      steps {
          build 'YOUR_PES2UG21CS456-1'
          sh 'g++ main.cpp -o output'
        }
    }
  stage('Test') {
      steps {
          sh './output'
      }
    }
  stage('Deploy') { 
      steps {
          echo 'deploy'
        }
      }
    }
  post{
      failure{
          error 'Pipeline failed'
        }
      }
    }
