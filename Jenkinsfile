pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('echo step') {
      steps {
        sh 'echo \'echo step\''
      }
    }
    stage('git checkout') {
      steps {
        git(url: 'https://github.com/ykoniev/training-ci', branch: 'master', credentialsId: '4fd64049-9b54-4d9c-af81-2ecc43955fb6', poll: true)
      }
    }
    stage('start app') {
      steps {
        sh '''cd flask-app;
docker-compose up -d --build'''
      }
    }
  }
}