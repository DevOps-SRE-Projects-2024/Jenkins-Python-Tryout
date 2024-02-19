pipeline {
    environment {
        GIT_REPO_URL = 'https://github.com/DevOps-SRE-Projects-2024/Jenkins-Python-Tryout.git'
    }
    agent any 
    stages {
        stage('Checkout') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'git_creds_id', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        git branch: 'main', credentialsId: 'git_creds_id', url: "${GIT_REPO_URL}"
                    }
                }
            }
        } 
        stage('Setup') {
            steps {
                script {
                    sh "pwd"
                    sh "pip3 install Flask"
                    sh "nohup python3 app.py &"  // Run Flask in the background
                }
            }
        }
    }
}
