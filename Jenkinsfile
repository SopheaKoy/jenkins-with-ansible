pipeline {
  agent any
  
  // Temporarily remove the tools section
  // tools {
  //   nodejs 'NodeJS 20'
  // }

  stages {
    stage('Clone Repository') {
      steps {
        checkout scm
      }
    }

    stage('Install Dependencies') {
      steps {
        // Use system npm if available
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    
    stage('Deploy Locally') {
      steps {
        // Kill any existing process using port 3000
        sh 'lsof -ti:3000 | xargs kill -9 || true'
        
        // Start the application in the background
        sh 'nohup npm run start > app.log 2>&1 &'
        
        // Let's verify it's running
        sh 'sleep 5 && lsof -i:3000 || echo "Warning: Process not detected on port 3000"'
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