pipeline {
    agent any
    
    stages {
      stage('build'){
        steps {
          sh 'echo building....'
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
