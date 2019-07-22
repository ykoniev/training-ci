pipeline {
  agent {
    node {
      label 'slave'
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
    stage('Change Current Dir') {
      steps {
        sh '''cd flask-app;
docker-compose down
docker-compose build flask-app
docker-compose run flask-app pytest -v --junit-xml=/var/opt/junit-report/report.xml
docker-compose down'''
      }
    }
    stage('Archive JUnit-formatted test results') {
      steps {
        sh '''
sudo rm -rf flask-app/junit-report'''
        junit(testResults: 'flask-app/junit-report/report.xml', allowEmptyResults: true)
      }
    }
    stage('Clean up') {
      steps {
        sh 'sudo rm -rf flask-app/junit-report'
      }
    }
  }
}