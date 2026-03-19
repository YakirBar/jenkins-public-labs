docker volume create jenkins_devops_lh

docker run -d --name jenkins -p 8090:8080 -p 3000:3000 -p 50000:50000 -v jenkins_devops_lh:/var/jenkins_home jenkins/jenkins:lts

/var/jenkins_home/secrets/initialAdminPassword

docker exec -it jenkins bash

whoami

- jenkins

cat /var/jenkins_home/secrets/initialAdminPassword

username: admin
password: secret
ur: http://localhost:8090

plugin:
Locale
Nodejs

docker exec -it --user root jenkins bash

whoami

- root

apt-get update
curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
apt-get install -y nodejs nano

apt-get install -y libatomic1 - for nodejs tool

-> ask about saving logs as volume

pipeline {
agent any

    stages {
        stage('check node version') {
            steps {
                sh '''
                    if command -v node > /dev/null 2>&1; then
                        echo "Node is installed"
                        node -v
                        npm -v
                    else
                        echo "Node is NOT installed, skipping..."
                    fi
                '''
            }
        }

        stage('verify index.js file') {
            steps {
                sh 'ls -la'
            }
        }

        stage('init node application') {
            steps {
                sh '''
                    if [ ! -f package.json ]; then
                        npm init -y
                    else
                        echo "package.json already exists"
                    fi
                '''
            }
        }

        stage('install express') {
            steps {
                sh 'npm install express || true'
            }
        }

        stage('run the application') {
            steps {
                sh '''
                    if [ -f index.js ]; then
                        node index.js
                    else
                        echo "index.js not found, skipping run"
                    fi
                '''
            }
        }
    }

}

    environment {
        NAME = "Yakir"
    }
        echo "Hello, ${NAME}!"

pipeline {
    agent any
    
    environment {
        NAME = "Yakir"
        FILE_NAME = "new-env.txt"
    }

    stages {
        stage('Hello my env') {
            steps {
                echo "Hello, ${NAME}"
            }
        }
        stage('create my env as file') {
            steps {
                sh "touch ${FILE_NAME}"
            }
        }
    }
}
























    stages {
        stage('explore env') {
            steps {
                echo "GitHub credentials: ${GITHUB_CREDENTIALS_USR} / ${GITHUB_CREDENTIALS_PSW}"
                echo "GitHub SSH credentials: ${GITHUB_CREDENTIALS_SSH_USR} / ${GITHUB_CREDENTIALS_SSH}"
            }
        }
    }




        GITHUB_CREDENTIALS_SSH = credentials('GitHub_SSH')
