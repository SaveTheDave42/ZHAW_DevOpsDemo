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
                withCredentials([string(credentialsId: 'GithubAccessToken', variable: 'GITHUB_TOKEN')]) {
                    sh '''
                        git config --global user.email "rappldav@students.zhaw.ch"
                        git config --global user.name "David Vocat"
                        git checkout main
                        git add -A
                        git diff-index --quiet HEAD || git commit -m "Jenkins build"
                        git push https://${GITHUB_TOKEN}@github.com/SaveTheDave42/ZHAW_DevOpsDemo.git
                    '''
                }
            }
        }
    }
}