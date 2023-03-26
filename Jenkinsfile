pipeline {
    agent any
    
    stages {
        stage('checkout') {
          
            steps {
                sh 'git branch -a'
                sh "git commit -m 'feat: comitei em'"
                sh 'git remote -v'
            }
        }
    }
    
}
