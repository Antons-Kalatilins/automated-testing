pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echo "Installing pip deps..."
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat "dir"
                bat "pip install -r requirements.txt"
                echo "all things are installed"
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo "Deploying to dev..."
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-dev & EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-dev -- --port 7001'
            }
        }
        stage('tests-on-dev') {
            steps {
                echo "Testing on dev..."
            }
        }
        stage('deploy-to-stg') {
            steps {
                echo "Deploying to stage..." 
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-dev & EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-stg -- --port 7002'
            }
        }
        stage('tests-on-stg') {
            steps {
                echo "Testing on stage..."      
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo "Deploying to preprod..."
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-preprod & EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-preprod -- --port 7003'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo "Testing on preprod..."    
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo "Deploying to prod..."
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-prod & EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-prod -- --port 7004'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo "Testing on prod..."    
            }
        }
    }
}
