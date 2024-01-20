pipeline {
  agent any
  stages {
    stage('install playwright') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npm install
          npm init playwright@latest
        '''
      }
    }
    stage('help') {
      steps {
        sh 'npx playwright test --help'
      }
    }
    stage('test') {
      steps {
        sh '''
          npx playwright test --list
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
