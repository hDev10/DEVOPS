pipeline {
    agent any
    
    stages {
      stage('checkout'){
        steps {
          sh 'git remote -v'
          sh 'git branch -a'
        }
      }
      stage('release'){
        steps{
          sh 'echo release ok'
        }
      }
        stage('tag') {
            steps {
                sh "git tag -a ${env.BUILD_NUMBER} -m 'Release version'"
                sh 'git push origin --tags'
            }
        }
    }
    
}
