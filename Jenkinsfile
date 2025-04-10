pipeline {
  agent any

  tools {
    nodejs 'NodeJS 20'
  }

  stages {
    stage('Clone Repository') {
      steps {
        checkout scm
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
  }
  // TODO: notify
  post {
    success {
      echo 'Application should now be running at http://localhost:3000'
    }
  }
}