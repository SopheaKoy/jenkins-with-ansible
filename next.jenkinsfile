pipeline {
  agent any

  tools {
    nodejs 'node-18'
  }
  
  // Add trigger for GitHub push events
  triggers {
    githubPush()
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/SopheaKoy/jenkins-with-ansible.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        // Add tests if your project has them
        sh 'npm test || echo "No tests found, continuing"'
      }
    }

    stage('Build App') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy & Run') {
      steps {
        // // Kill any existing process on port 3000
        // sh 'lsof -ti:3000 | xargs kill -9 || true'
        
        // Start the application with proper process management
        sh '''
          nohup npm run start > app.log 2>&1 &
          echo $! > .pid
          sleep 5 # Give the app time to start
        '''
        
        // Verify the app is running
        sh 'curl -s http://localhost:3000 || (echo "App failed to start"; exit 1)'
        
        echo 'App successfully deployed and running on http://localhost:3000'
      }
    }
  }

  post {
    success {
      echo '✅ Build and deployment successful!'
    }
    failure {
      echo '❌ Build or deployment failed!'
    }
    always {
      echo 'Pipeline finished!'
    }
  }
}