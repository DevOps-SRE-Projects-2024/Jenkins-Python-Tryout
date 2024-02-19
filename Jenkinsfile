
pipeline {
    environment {
        GIT_REPO_URL = 'https://github.com/DevOps-SRE-Projects-2024/Jenkins-Python-Tryout.git'
        // Replace 'username', 'password', 'yourusername', and 'yourrepository' with your actual values
    }
 agent any 
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
    }
    stage('Setup') {
            steps {
                script {
                    // Set up virtual environment and install dependencies
                    sh "pwd"
                    sh "sudo su -"
                    sh "apt-get update -y"
                    sh "apt-get install python3 python3-pip -y"
                    sh "pip3 install Flask"
                    sh "python3 app.py"
                }
            }
        }
  }
}
