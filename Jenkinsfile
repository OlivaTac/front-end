pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'apk update && apk add nodejs'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
        sh 'npm test'
      }
    }

    stage('Package') {
      steps {
        echo 'Packaging....'
        sh 'npm run package'
        archiveArtifacts(artifacts: '**/distribution/*.zip', fingerprint: true)
      }
    }

  }
  tools {
    nodejs 'NodeJS 4.8.6'
  }
}