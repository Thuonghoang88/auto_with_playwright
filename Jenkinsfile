pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh '''
          export PATH="/usr/local/bin/npm:/usr/local/bin/node:/usr/local/bin:$PATH"
          npx playwright test jenkins-homepage.spec.ts
        '''
      }
    
    }
  }
}
