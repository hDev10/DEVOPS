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
                sh 'git config --global user.email "lucasf3rnando@gmail.com"'
                sh 'git config --global user.name "Lucas"'
                sh "git tag -a ${env.BUILD_NUMBER} -m 'Release version'"
                sh 'git push origin --tags'
            }
        }
    }
    
}
