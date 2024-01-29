pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npm i -D @playwright/test allure-playwright --force
          npm run testCase
          npx allure serve allure-results
        '''
      }
      post { 
        always { 
          publishHTML([ allowMissing: false,  alwaysLinkToLastBuild: true,  keepAll: true,  reportDir: 'allure-report',  reportFiles: 'index.html',  reportName: 'test report',  reportTitles: ''])
        } 
      }
    
    }
  }
}
