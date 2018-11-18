pipeline {
    agent {
        label 'linux && swarm'
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
            withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '40c0c400-d6a5-456d-9ff1-77ab9c4ba9ee', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
          }
        }
      }
    }
}
