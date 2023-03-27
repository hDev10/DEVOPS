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
            ...
        }
        stage('Adding the version to the latest commit as a tag') {
            steps {
                withCredentials([[$class: 'UsernamePasswordMultiBinding',
                        credentialsId: '68c68f2c-ce30-438c-bca8-ef066ac53caf',
                        usernameVariable: 'GIT_USERNAME',
                        passwordVariable: 'GIT_PASSWORD']]) {
                    sh '''
                        git config --global credential.username $GIT_USERNAME
                        git config --global credential.helper '!f() { echo password=$GIT_PASSWORD; }; f'
                    '''
                    sh """
                        git tag ${version}
                        git push ${repoUrl} --tags
                    """
                }
            }
        }
    }
}
