pipeline {
  agent any

  tools {
    nodejs 'NodeJS 18'  // Optional, if using NodeJS plugin
  }

  stages {
    stage('Clone Repository') {
      steps {
        git 'https://github.com/SopheaKoy/jenkins-with-ansible.git'
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
}