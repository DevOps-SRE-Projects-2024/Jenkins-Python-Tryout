
pipeline {
  agent {
    docker {
      image 'abhishekf5/maven-abhishek-docker-agent:v1'
      args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
    }
  }
  stages {
    stage('Checkout') {
      steps {
        sh 'echo passed'
      }
    }
    stage('Setup') {
            steps {
                script {
                    // Set up virtual environment and install dependencies
                    sh "pwd"
                    sh "pip install -r requirements.txt"
                }
            }
        }
    }
  }
