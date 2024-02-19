
pipeline {
    environment {
        GIT_REPO_URL = 'https://github.com/DevOps-SRE-Projects-2024/Jenkins-Python-Tryout.git'
        // Replace 'username', 'password', 'yourusername', and 'yourrepository' with your actual values
    }
  agent {
    docker {
      image 'abhishekf5/maven-abhishek-docker-agent:v1'
      args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
    }
  }
  stages {
    stage('Checkout') {
      steps {
        script {
                    // Use 'withCredentials' to provide username and password
                    withCredentials([usernamePassword(credentialsId: 'git_creds_id', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        git branch: 'main', credentialsId: 'git_creds_id', url: "${GIT_REPO_URL}"
                    }
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
}
