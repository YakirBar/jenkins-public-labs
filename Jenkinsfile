pipeline {
    agent any

    tools {
        nodejs 'my-node-tool'
    }

    environment {
        NAME = "Yakir"
        GITHUB_CREDENTIALS = credentials('Github_PAT_Yakir')
    }
    
    stages {
        stage('show github cred') {
            steps {
                echo "GitHub credentials: ${GITHUB_CREDENTIALS_USR} / ${GITHUB_CREDENTIALS_PSW}"
            }
        }
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