pipeline {
    agent {
    label 'devops1-wahyu'
    }

    
    tools {
    nodejs 'nodejs'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/traningdevopsidn/simple-apps.git'
            }
        }
        stage('Build') {
            steps {
                sh '''cd apps
                npm install'''
            }
        }
        stage('Testing') {
            steps {
                sh '''cd apps
                npm test
                npm run test:coverage'''
            }
        }
        /* stage('Code Review') {
            steps {
            sh '''cd apps
            sonar-scanner \\
            -Dsonar.projectKey=Simple-Apps \\
            -Dsonar.sources=. \\
            -Dsonar.host.url=http://172.23.10.15:9000 \\
            -Dsonar.login=sqp_cb62f92fd4e509f3c960edd332f7cba46438669e'''
            }
        } */
        stage('Deploy compose') {
            steps {
                sh '''
                docker compose build
                docker compose up -d
                '''
            }
        }
    }
}