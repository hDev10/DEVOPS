def branch = 'main'
def repoUrl = 'https://github.com/hDev10/DEVOPS'

pipeline {
    agent any
    stages {
        stage('Checkout example-app') {
            steps {
                git branch: branch,
                credentialsId: '68c68f2c-ce30-438c-bca8-ef066ac53caf',
                url: repoUrl
            }
        }
        stage('Create version') {
            steps {
                script {
                    currentDateTime = sh script: """
                        date +"-%Y%m%d_%H%M"
                        """.trim(), returnStdout: true
                    version = currentDateTime.trim()  // the .trim() is necessary
                    echo "version: " + version
                }
            }
        }
        stage('Build and deploy') {
            steps{
            sh 'echo olla mundo'
            }
        }
        stage('Adding the version to the latest commit as a tag') {
                 environment { 
                GIT_TAG = "jenkins-${env.BUILD_NUMBER}"
            }
            steps {
                sh('''
                    git config user.name 'my-ci-user'
                    git config user.email 'my-ci-user@users.noreply.github.example.com'
                    git tag -a ${env.GIT_TAG} -m "[Jenkins CI] New Tag"
                ''')
                
                sshagent(['my-ssh-credentials-id']) {
                    sh("""
                        #!/usr/bin/env bash
                        set +x
                        export GIT_SSH_COMMAND="ssh -oStrictHostKeyChecking=no"
                        git push origin ${env.GIT_TAG}
                     """)
                }
            }
        }
    }
}