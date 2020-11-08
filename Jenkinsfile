pipeline {
  agent any

  stages {
    stage ('Unit & Report') {
      steps {
        sh label: 'Unittest by Golang', script: '''cd store-service
        go mod download
        go test ./... -v 2>&1 | go-junit-report > report.xml'''
      }
      post {
        always {
            junit 'store-service/report.xml'
        }
      }
    }

    stage ('Docker Compose') {
      steps {
        sh label: 'docker-compose', script: '''docker-compose up -d --build --force-recreate'''
      }
      post {
        always {
          sh label: 'docker-compose', script: '''docker-compose down'''
        }
      }
    }
  }
}