pipeline {
    agent any
    
    stages {
      stage('checkout'){
        steps {
          git 'init'
          git 'remote add origin https://github.com/hDev10/DEVOPS'
        }
      }
      stage('release'){
        steps{
          sh 'echo release ok'
        }
      }
        stage('tag') {
            steps {
                sh 'git tag -a v1.0.0 -m "Release version 1.0.0"'
                sh 'git push origin --tags'
            }
        }
    }
    
}
