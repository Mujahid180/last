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
deploy adapters: [tomcat9(credentialsId: 'b10b0d3f-8411-4a5b-a856-09f8ea2cfb93', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war'}
 }
 }
 }
}

