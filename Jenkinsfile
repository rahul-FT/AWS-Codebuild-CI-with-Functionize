pipeline {
    agent none
    stages {
        stage('Stage 1') {
            agent { docker 'node:9.11.1' }
            steps {
                echo 'Hello, From First Stage'
                sh 'node --version'
            }
        }
        stage('Stage 2') {
            agent { docker 'node:9.11.1' }
            steps {
                echo 'Hello, From Second Stage'
                sh 'node --version'
            }
        }
    }
}
