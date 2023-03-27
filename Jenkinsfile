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
            steps {
                sh 'echo olla mundo'
            }
        }
        stage('Adding the version to the latest commit as a tag') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'git_auth', keyFileVariable: '/home/azship1/.ssh/id_rsa2.pub
', passphraseVariable: '', usernameVariable: '')]) {
                    sh("""
                    git config user.name 'hDev10'
                    git config user.email 'lucasf3rnando@gmail.com'
                    git tag -a ${env.BUILD_NUMBER} -m 'New Tag'
                       git push origin ${env.BUILD_NUMBER} --tags 
               """)
                }
            }
        }
    }
}