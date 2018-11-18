pipeline {
    agent {
        label 'JenkinsSlaveGroup'
    } 

    stages {
        stage('Unit Tests') {
          steps {
            sh 'ant -f test.xml -v'
            junit 'reports/result.xml'
          }
        }
        stage('Build') {
        steps {
            sh 'ant -f build.xml -v'
          }
        }
        stage('Deploy') {
        steps {
            sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-*.jar s3://seis665-assignment9-zaaberg/'
          }
        }        
        stage('Report') {
        steps {
            sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
          }
        }
   
    }
}
