pipeline {
    agent any
    
    stages {
        stage('HELLO') {
            steps {
                echo 'HELOOOOOOOOOOOOO'
            }
        }
    }
    
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
