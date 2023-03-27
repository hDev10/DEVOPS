def repoUrlWithAuth = "https:/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@github.com/hDev10/DEVOPS.git"
def sourceBranch = "main"

pipeline {
    agent any
    stages {

        stage('Build and deploy') {
            steps {
              git url: 'https://github.com/hDev10/DEVOPS', branch: 'main',
              credentialsId: 'git_auth'
            }
        }
        stage('TESTE'){
          steps{
            withCredentials([gitUsernamePassword(credentialsId: 'git_auth', gitToolName: 'git-tool')]) {
            sh "git tag -a ${env.BUILD_NUMBER} -m 'message'"
            sh "git push origin --tags"
            }
          }
        }

    }
}