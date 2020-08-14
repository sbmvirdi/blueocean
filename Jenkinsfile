  
pipeline {
      agent any
      stages {
            stage('Lint HTML.'){
                  steps {
                        sh "tidy -q -e *.html"
                  }
            }
            stage('Upload to AWS.') {
                steps {
                    withAWS(region:'ap-south-1',credentials:"sbmvirdi") {
                        s3Upload(file:'index.html', bucket:'jenkins-india', path:'index.html')
                    }

                    sh 'echo "Hello World"'
                    sh '''
                        echo "Multiline shell steps works too"
                        ls -lah
                    '''
                  }

            }
        
      }
}