pipeline {
  agent any

  tools {
    nodejs 'NodeJS 18'  // Optional, if using NodeJS plugin
  }

  stages {
    stage('Clone Repository') {
      steps {
        git 'https://github.com/your-user/your-nextjs-repo.git'
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

    stage('Export (Optional for Static)') {
      steps {
        sh 'npm run export'
      }
    }

    stage('Test (Optional)') {
      steps {
        sh 'npm test'
      }
    }
  }
}