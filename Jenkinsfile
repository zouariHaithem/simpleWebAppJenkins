pipeline {
  agent any
  tools {
    maven 'maven3'
  }
  stages {
  stage ('clone') {
        steps {
          git 'https://github.com/zouariHaithem/simpleWebAppJenkins.git'
        }
      }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: '14019c80-40d8-48d8-adac-e33325b5a049', path: '', url: 'http://localhost:9090')], contextPath: '/pipeline', onFailure: false, war: '**/*.war'
        }
      }
    }
  }
}