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
        stage('Env Init') {
            steps {
                sh 'composer update'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }
        stage('php test') {
            steps {
                sh 'php artisan test'
            }
        }
        // stage('Checkout Repo') {
        //     steps {
        //         git url: 'https://github.com/monosparta/gohiking-server.git', branch: 'main'
        //         sh 'ls -al'
        //     }
        // }
        // stage('Make Zip Artifacts') {
        //     steps {
        //         zip zipFile: 'gohiking-server.zip'
        //     }
        // }
    }
    
    post {
        always {
            archiveArtifacts artifacts: '*.json', fingerprint: true
        }
    }
}
