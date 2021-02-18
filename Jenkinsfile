// Workflow

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Check Env') {
            steps {
                sh 'php --version'
                sh 'composer --version'
            }
        }
        stage('Build') {
            steps {
                sh 'composer update'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
                sh 'php artisan test'
            }
        }
        stage('Make Zip Artifacts') {
           steps {
               zip zipFile: 'gohiking-server.zip', overwrite: false
           }
        }
    }
    
    post {
        always {
            archiveArtifacts artifacts: '*.zip', fingerprint: true
        }
    }
}
