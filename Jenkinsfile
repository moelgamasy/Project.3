
pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World!!"'
                 sh '''
                     echo "Multiline steps works too !!"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
                
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'gamasy1') {
                  sh 'echo "Uploading content"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pro3udacity')
                  }
              }
         }
     }
}
