pipeline {
    agent any
    stages {
        stage('Checkout') { 
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SaveTheDave42/ZHAW_DevOpsDemo']])
                sh 'echo checkout'
            
            }
        }
        stage('Test') { 
            steps {
                sh 'echo test'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo deploy'
            }
        }
        stage('Save to GitHub') { 
            steps {
                sh 'git config --global user.email "rappldav@students.zhaw.ch"'
                sh 'git config --global user.name "David Vocat"'
                sh 'git add -A'
                sh 'git diff-index --quiet HEAD || git commit -m "Jenkins build"'
                sh 'git push'
            }
        }
    }
}