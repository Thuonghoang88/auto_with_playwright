pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npm run testCase
        '''
      }
      post { 
        always { 
          publishHTML([ allowMissing: false,  alwaysLinkToLastBuild: true,  keepAll: true,  reportDir: 'playwright-report',  reportFiles: 'index.html',  reportName: 'test report',  reportTitles: ''])
        } 
      }
    
    }
  }
}
