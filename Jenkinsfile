pipeline {
  agent {
    label 'windows'
  }

  environment {
    NODE_OPTIONS = '--max-old-space-size=2048'
  }

  stages {
    stage('Checkout Code') {
      steps {
        git url: 'https://github.com/Anandh-developer/Wdiorepo.git', branch: 'main'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'npm run wdio'
      }
    }

    stage('Cleanup') {
      steps {
        bat 'rd /s /q node_modules'
      }
    }
  }

  post {
    always {
      echo 'Pipeline finished. Cleaning up workspace.'
      cleanWs()
    }
  }
}
