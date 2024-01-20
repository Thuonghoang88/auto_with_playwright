pipeline {
  agent any
  stages {
    stage('install playwright') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    stage('test') {
      steps {
        sh '''
          npx playwright test
        '''
      }
      post {
        success {
          archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
          sh 'rm -rf *.png'
        }
      }
    }
  }
}
