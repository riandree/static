pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'eu-central-1',credentials:'aws-static') {
            sh 'echo "Uploading content with AWS creds"'
            s3Upload(payloadSigningEnabled: true, 
                     file:'index.html', 
                     bucket:'rieck-andre-udacity-jenkins-pipelines-on-aws')
        }
      }           
    }
  }
}
