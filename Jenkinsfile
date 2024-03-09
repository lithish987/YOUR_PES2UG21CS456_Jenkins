pipeline {
  agent {
    docker {
      image 'node:14'
          }
      }
  stages {
    steps {
      stage('Clone repository') {
        git branch: 'main',
        url: 'https://github.com/<user>/<repo>.git'
      }
  }
stage('Install dependencies') {
steps {
sh 'npm install'
}
}
stage('Build application') {
steps {
sh 'npm run build'
}
}
stage('Test application') {
steps {
sh 'npm test'
}
}
stage('Push Docker image') {
steps {
sh 'docker build -t <user>/<image>:$BUILD NUMBER .'
sh 'docker push <user>/<image>:$BUILD NUMBER'
}
}
}
}
pipeline {
agent any
stages {
stage('Build') {
steps {
}
}
sh 'mvn clean install'
echo 'Build Stage Successful'
stage('Test') {
steps {
sh 'mvn test'
echo 'Test Stage Successful'
post {
always {
junit 'target/surefire-reports/*.xml'
}
}
}
}
stage('Deploy') {
steps {
sh 'mvn deploy'
echo 'Deployment Successful'
}
}
post {
failure {
echo 'Pipeline failed'
}
}
}
