pipeline {
  agent {
    node {
      label 'node 1'
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
        git(url: 'https://github.com/ykoniev/training-ci', branch: 'master', credentialsId: '1a28fc22-8d41-479c-9abd-d44db5fadfad	', poll: true)
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