pipeline {
    agent any

    stages {
        stage('Build') {
          steps {
            sh 'ant'
          }
        }
        stage('Test') {
        steps {
            junit 'reports/*.xml'
          }
        }
    }
}
