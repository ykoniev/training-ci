pipeline {
  agent {
    node {
      label 'node 1'
    }

  }
  stages {
    stage('node 1') {
      steps {
        sh '''cd flask-app;
docker-compose up -d --build'''
      }
    }
  }
}