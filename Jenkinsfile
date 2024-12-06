pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: 'd97c36d2-d7a9-439f-a035-c88294125145', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd', war: '**/*.war'}
 }
 }
 }
}

