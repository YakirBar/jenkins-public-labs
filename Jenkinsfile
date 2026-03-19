pipeline {
    agent any

    tools {
        nodejs 'my-node-tool'
    }
    
    stages {
        stage('pwd') {
            steps {
                sh "pwd"
            }
        }
        stage('show files:') {
            steps {
                sh "ls -la"
            }
        }
        stage('run the application:') {
            steps {
                sh "npm init -y"
                sh "npm i express"
                sh "node index.js"
            }
        }
    }
}