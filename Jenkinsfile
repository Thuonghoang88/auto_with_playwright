pipeline {
  agent any
  stages {
    stage('install playwright') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npm install
          npm run testCase
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
