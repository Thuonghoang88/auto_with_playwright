pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npm i -D @playwright/test allure-playwright --force
          npm run testCase
        '''
      }
      post { 
        always { 
           publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'playwright-report', reportFiles: 'index.html', reportName: 'OPS Report'])
        } 
      }
    
    }
  }
}
