pipeline {
    agent any

    environment {
        APP_ENV = "development"
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/ap786771/flask-git-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python3 app.py &'
            }
        }
    }
}
