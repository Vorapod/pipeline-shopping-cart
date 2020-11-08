pipeline {
  agent any

  stages {
    stage ('Unit & Report') {
      steps {
        sh label: 'Unittest by Golang', script: '''cd store-service
        go mod download
        go test ./... -v 2>&1 | go-junit-report > report.xml'''
      }
    }
  }
}