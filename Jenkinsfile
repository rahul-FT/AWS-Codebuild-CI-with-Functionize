Jenkinsfile (Declarative Pipeline)
pipeline {
    agent { docker { image 'node:9.11.1' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
    }
}
