def branch = 'main'
def repoUrl = 'https://github.com/hDev10/DEVOPS'

pipeline {
    agent any
    stages {

        stage('Build and deploy') {
            steps {
                sh 'echo olla mundo'
            }
        }
        stage('Adding the version to the latest commit as a tag') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'git_autentication', keyFileVariable: '/home/azship1/.ssh/id_rsa2', passphraseVariable: '', usernameVariable: '')]) {
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