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
            echo 'reports/*.xml'
          }
        }
    }
}
