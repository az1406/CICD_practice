pipeline {
  agent any

  environment {
    NPM_TOKEN = credentials('NPM_TOKEN')
  }

  stages {
    stage('Build') {
      steps {
        echo 'Installing dependencies...'
        sh 'npm ci'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'npm test'
      }
    }

    stage('Publish') {
      steps {
        echo 'Publishing to NPM...'
        sh '''
          echo "//registry.npmjs.org/:_authToken=${NPM_TOKEN}" > .npmrc
          npm publish
        '''
      }
    }
  }
}
